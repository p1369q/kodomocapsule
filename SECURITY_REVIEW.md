# v299 海外アクセス・bot対策に向けたセキュリティ点検レビュー

確認日: 2026-07-06  
対象バージョン: アプリ本体は v298 のまま、セキュリティ点検ドキュメントとして v299 を追加

## 目的と判断

Google Analytics で海外からのアクセスが見えても、それだけで危険とは限りません。検索エンジン、SNSプレビュー、Firebase Hosting上の公開サイト巡回、海外在住の日本人ユーザー、VPN・翻訳経由、悪意ある探索が混在する可能性があります。

今回の判断は次のとおりです。

- 海外IPの一律ブロックは行わない。
- 日本国外アクセスの拒否は行わない。
- App Check、reCAPTCHA、Firebase設定、Stripe設定、Cloud Run URL、Firestore / Storage / Auth / Analytics の設定変更は行わない。
- アプリ本体の `index.html` は変更せず、まず運用者向けの点検結果として記録する。

## 確認したファイル

- `AGENTS.md`
- `README.md`
- `CHANGELOG.md`
- `index.html`

v303で次の設定ファイルをリポジトリ管理に追加しました。

- `firebase.json`
- `firestore.rules`
- `storage.rules`

ただし、Hosting / Firestore Rules / Storage Rules の最終判断は、Firebase Console側の実設定とGitHub上のRulesがズレていないかを必ず確認してください。

## 1. Firebase Hosting 設定レビュー

### 確認結果

v303で `firebase.json` を追加し、Hosting の公開ディレクトリ、redirects、rewrites をGitHub管理対象にしました。

### 問題なしだった点

- このリポジトリ上では、`public/` 配下に意図せず秘密情報やバックアップファイルを置いている状態は確認できませんでした。
- `index.html` 内に `public/assets/...` 形式の参照は確認されませんでした。

### 注意が必要な点

- Firebase Hosting をこのリポジトリ以外からデプロイしている場合、実際の `firebase.json` と公開ディレクトリを別途確認する必要があります。
- GitHub管理上の古い `index-backup.html` は削除済みです。本番公開対象 `public/` にバックアップHTMLを置かない運用を確認してください。
- v303で追加した `firebase.json` にはセキュリティヘッダーやキャッシュ制御の `headers` 設定は含めていないため、必要に応じて別タスクで確認してください。

### 運用確認ポイント

- GitHub管理上の古い `index-backup.html` は削除済みであること。
- 本番公開対象 `public/` にバックアップHTMLを置かない運用を維持すること。
- `/index-backup.html` はFirebase Hostingのredirectで `/` に飛ばす設定を維持すること。
- Firebase Hosting の `public` ディレクトリが意図した場所か。
- `rewrites` / `redirects` / `headers` に不自然な転送や過度に長いキャッシュがないか。
- HTMLには短いキャッシュ、画像など静的アセットには適切なキャッシュが設定されているか。
- `index-backup.html`、ローカル作業メモ、秘密鍵、環境変数ファイルが公開対象になっていないか。

## 2. Firestore Rules レビュー

### 確認結果

v303で `firestore.rules` を追加し、Firestore Rules をGitHub管理対象にしました。厳密な安全性は、Firebase Console側の実設定とGitHub上のRulesがズレていないかを確認してください。

`index.html` 側の実装を見る限り、通常保存はログイン済みユーザーと `currentSession.familyId` を前提に、`families/{familyId}` 配下の `children`、`categories`、`artworks` に書き込む構造です。ゲストモードでは保存系処理の先頭で保存不可アラートを出し、Firestore書き込みへ進まないガードがあります。

### 問題なしだった点

- ゲストモード開始時はローカル配列にサンプルデータを入れるだけで、Firestore書き込みは発生しません。
- 子ども、カテゴリ、作品の保存処理はゲストモード時に早期 return します。
- 作品保存は `currentSession` がない場合に return し、保存先は `families/{currentSession.familyId}/artworks` 配下です。

### 注意が必要な点

- クライアント側ガードはUX上の保護であり、セキュリティ境界ではありません。Firestore Rules で未ログイン・他家族IDへの直接アクセスを必ず拒否する必要があります。
- 家族共有、招待コード、参加申請、管理者向け操作はクライアントに複数の書き込み経路があります。Rules 側で `request.auth.uid`、参加中の familyId、権限ロールを必ず検証してください。
- botや悪意あるユーザーが正規ログインした場合に備え、Rules だけでなく使用量アラートや異常検知も必要です。

### Firebase Consoleで確認すべきRules観点

- `request.auth != null` が本番データ書き込みの最低条件になっているか。
- `users/{uid}` は本人のみ読み書き可能か。
- `families/{familyId}` とサブコレクションは、作成者または参加メンバーのみ読めるか。
- 家族共有の権限ロールに応じて、追加・編集・削除が制御されているか。
- `familyInvites` と `familyJoinRequests` が過剰に読み取り公開されていないか。
- 管理者向けや招待コード関連の更新を、任意ユーザーが横取り・改ざんできないか。
- 大量書き込みを完全には止められなくても、他人のデータ破壊や横断読み取りができない設計になっているか。

## 3. Storage Rules レビュー

### 確認結果

v303で `storage.rules` を追加し、Storage Rules をGitHub管理対象にしました。厳密な安全性は、Firebase Console側の実設定とGitHub上のRulesがズレていないかを確認してください。

`index.html` 側では、ログイン後の作品保存時に `families/{familyId}/artworks/{artworkId}/...` へPDFまたは画像をアップロードします。ゲストモードでは作品保存処理に入る前に return するため、登録なし利用から Storage アップロードへ進まない構成です。

### 問題なしだった点

- 登録なし利用のサンプル素材は Firebase Storage ではなく静的パス `assets/guest-samples/...` を参照しています。
- ゲストモードでは作品保存前に早期 return するため、通常操作では Storage アップロードが発生しません。
- ユーザーアップロードの保存先は `families/{familyId}/artworks/...` 形式で、ゲストサンプル素材とはパスが分離されています。

### 注意が必要な点

- Storage Rules が未確認のため、未ログインアップロード拒否、他家族ファイルの読み取り拒否、MIME type、ファイルサイズ上限は Firebase Console で必ず確認してください。
- クライアント側は `uploadString(..., "data_url")` でアップロードします。Rules 側で `request.resource.size` と `request.resource.contentType` を制限しないと、容量消費リスクが残ります。
- PDFと画像の保存を許可する場合でも、想定外のMIME typeや大きすぎるファイルは拒否してください。

### Firebase Consoleで確認すべきRules観点

- 未ログインユーザーが任意パスへアップロードできないか。
- `families/{familyId}/...` はその家族の参加ユーザーだけ読み書きできるか。
- ゲストサンプルの静的ファイルとユーザー私的アップロードが同じStorageパスに混ざっていないか。
- 画像・PDFのMIME typeとサイズ制限が設定されているか。
- 削除権限が編集権限・管理権限と一致しているか。

## 4. 登録なし利用レビュー

### 確認結果

登録なし利用は `enterGuestMode()` で `isGuestMode = true` にし、ローカル配列へサンプルの子ども・カテゴリ・作品を入れる構成です。Firestore / Storage への保存処理はゲストモードで早期 return します。

維持されているサンプル参照は次のとおりです。

- `assets/guest-samples/flat/first-drawing.png`
- `assets/guest-samples/flat/hiragana-test.png`
- `assets/guest-samples/flat/math-print.png`
- `assets/guest-samples/flat/tanabata-craft.jpg` は今回の `index.html` 参照には含まれていませんでした。
- `assets/guest-samples/3d/paper-cup-craft.png`
- `assets/guest-samples/3d/tanabata-decoration.png`
- `assets/guest-samples/pdf/kindergarten-notice.pdf`
- `assets/guest-samples/pdf/kindergarten-notice-page1.png`

### 問題なしだった点

- `public/assets/...` 形式の参照は確認されませんでした。
- 登録なし利用でFirestoreに書き込む処理は確認されませんでした。
- 登録なし利用でStorageにアップロードする処理は確認されませんでした。
- サンプル閲覧は静的アセット参照中心のため、通常の閲覧だけでFirestore / Storage課金が増えにくい構成です。

### 注意が必要な点

- 静的ファイルへのbotアクセスはHosting転送量としては発生します。GA4だけでなくHostingの転送量も定期的に確認してください。
- `tanabata-craft.jpg` は維持すべきHTML参照として依頼文にありましたが、現在の `index.html` には見つかりませんでした。過去バージョンとの差分意図がある場合は別タスクで確認してください。

## 5. Cloud Run / Stripe 関連レビュー

### 確認結果

HTML側のCheckout作成処理は `redirectToStripeCheckout()` にまとまっています。

- ゲストモードではCheckout作成前に保存不可アラートで return します。
- ログイン中の `auth.currentUser` と `currentSession.familyId` を確認してから Cloud Run にPOSTします。
- Cloud Run URL は `https://create-checkout-session-486206364077.us-central1.run.app` です。
- 戻り先は `https://kodomocapsule.com/` を基準に、`success_url` / `cancel_url` と互換用の `successUrl` / `cancelUrl` を送っています。
- HTML内に Stripe Price ID の直接指定は確認されませんでした。Price ID はCloud Run側で管理されている可能性があります。

### 問題なしだった点

- v288で整理された本番URLへの復帰処理は維持されています。
- ゲストモードや未ログイン状態ではCheckout作成APIに進みにくいガードがあります。
- 今回、Stripe Price ID、Checkout URL、Cloud Run URL、課金処理、プレミアム判定ロジックは変更していません。

### 注意が必要な点

- Cloud Run URLは公開されているため、botが直接POSTする可能性はあります。最終的な防御はCloud Run側でFirebase ID token検証、familyId権限確認、レート制限、Stripe Session作成の冪等性・重複抑制を行う必要があります。
- HTML側のガードだけではAPI直叩き対策にはなりません。
- App Checkを導入する場合でも、Cloud Run側の認証・認可チェックの代替にはなりません。

## 6. GA4 / Firebase Console / Stripe で見るべき項目

### GA4

- 国別アクセスと地域別アクセス。
- 新規ユーザー / リピーターの比率。
- 参照元、検索、SNS、direct、unknownの偏り。
- 平均エンゲージメント時間。
- 極端に短い滞在で大量アクセスしている国・参照元。
- `login_click`、`guest_start`、プレビュー系イベント、`stripe_checkout_click` の発火数。
- ページビューに対してイベントが極端に少ないbotらしいアクセス。
- 短時間に同一国・同一参照元からイベントが急増していないか。

### Firebase Authentication

- Googleログイン試行数の急増。
- 失敗ログインや不自然なアカウント作成の増加。
- 見慣れない地域からのログインが通常利用と一致するか。

### Firestore

- ドキュメント読み取り / 書き込み / 削除数の急増。
- `families`、`familyInvites`、`familyJoinRequests`、`users` など権限関連コレクションの異常増加。
- 1ユーザーまたは1 familyId に偏った大量書き込み。

### Firebase Storage

- 保存容量の急増。
- ダウンロード転送量の急増。
- 画像・PDF以外の不審なMIME type。
- 1 familyId 配下に偏った大量アップロード。

### Cloud Run

- Checkout作成APIのリクエスト数。
- 4xx / 5xx エラー率。
- Firebase ID tokenなし、または権限不一致で拒否されたリクエスト数。
- 同一IP・同一uid・同一familyIdからの短時間連続リクエスト。

### Stripe

- Checkout Session作成数。
- Checkout完了率。
- 同一メールアドレスまたは同一client_reference_idからの連続Session作成。
- 未完了Sessionの急増。
- Webhookの失敗数とリトライ数。

## 7. App Check 導入余地と注意点

### 今回の判断

今回は App Check を導入・強制しません。まずモニタリングとRules確認を優先し、正規ユーザーへの影響を把握してから段階導入するのが安全です。

### 将来導入する場合の対象

- Firestore
- Firebase Storage
- Cloud Functions
- Cloud Run連携API

Webアプリでは reCAPTCHA Enterprise などのプロバイダ選定、許可ドメイン設定、ローカル開発やGitHub Pages / Firebase Hosting / 独自ドメインの扱いを整理する必要があります。

### 注意点

- いきなり強制適用すると、iPhone / iPad / PCブラウザの一部環境、ブラウザ拡張、プライバシー設定、古いWebViewで正規ユーザーが利用できなくなる可能性があります。
- まずはモニタリングモードで正規リクエストがどの程度App Check token付きになるか確認してください。
- 強制前に、Firebase Hostingドメイン、独自ドメイン `kodomocapsule.com`、必要ならGitHub Pagesドメインを許可対象として整理してください。
- App Checkはbot対策の一部であり、Firestore Rules、Storage Rules、Cloud Run側認証・認可、Stripe側検証の代替ではありません。

## 今すぐやらない方がよい対策

- 海外IPの一律ブロック。
- 日本国外アクセスの拒否。
- App Checkの即時強制。
- reCAPTCHAの全導線への強制追加。
- Firebase configの差し替え。
- Stripe Price ID、Checkout URL、Cloud Run URLの変更。
- 課金処理、プレミアム判定、保存容量制限、Minecraft生成、家族共有、ログイン後保存処理の変更。

## 将来検討する対策

- Firebase Consoleで実Rulesを確認し、必要ならRulesのテストケースを追加する。
- Firebase Hostingのセキュリティヘッダーとキャッシュ方針を明文化する。
- Cloud Run側でFirebase ID token検証、familyId権限確認、レート制限、重複Checkout抑制を確認する。
- App Checkをモニタリングから段階導入する。
- Firestore / Storage / Cloud Run / Stripeの使用量アラートを設定する。
- GA4でbotらしい参照元や異常イベントを定期確認する運用チェックリストを作る。

## 次に必要な実機・運用確認

- PC / iPhone / iPad で通常ログイン、ゲスト体験、作品閲覧、プレビュー導線が従来どおりか確認する。
- Firebase ConsoleでFirestore RulesとStorage Rulesの本番適用内容を確認する。
- Firebase Hostingの実際の公開ディレクトリと公開ファイル一覧を確認する。
- Cloud RunログでCheckout作成APIへの不審な連続アクセスがないか確認する。
- Stripe Dashboardで未完了Checkout Sessionが急増していないか確認する。
