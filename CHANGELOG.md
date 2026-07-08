# CHANGELOG

## v316

* スマホ幅限定で下部固定ナビを追加
* ギャラリー / 写真一覧 / ＋追加 / 家族 / 設定 にアクセスしやすくした
* 中央の＋追加を目立つ丸ボタン風に調整
* iPhoneの下部セーフエリアと本文下余白に配慮
* PC表示は原則維持
* Firebase / Firestore / Storage / Stripe / Cloud Run / 家族共有 / 保存処理は変更なし
* Minecraft生成ロジックは変更なし
* JavaScript構文チェック済み

## v315

* Minecraftプレビュー画面の調整メニューを、iPhone幅でも押しやすい大きめのボタン風UIに整理
* 「見た目とサイズを調整」の文言を「サイズや額縁を変える」に変更
* Minecraft保存/共有ボタンから番号を外し、「Minecraftに保存」「アドオンを共有」に変更
* 手順案内内の保存/共有ボタン名も番号なしの表現に統一
* v314のプレビュー固定レイアウトは維持
* 「現在の見え方」ミニプレビューは復活させていない
* モブ風作品 β は引き続き公開UIから非表示
* 詳細な見た目調整メニューは復活させていない
* Firebase / Firestore / Storage / Stripe / Cloud Run / 家族共有 / 保存処理は変更なし
* JavaScript構文チェック済み

## v314

* Minecraftプレビュー画面で、タイトル・説明文エリアは固定せずスクロールさせるようにした
* 固定対象を「マイクラでの見え方」プレビューカードに限定
* iPhone幅でプレビューが画面を占有しすぎないよう調整
* 「現在の見え方」ミニプレビューは復活させていない
* モブ風作品 β は引き続き公開UIから非表示
* 詳細な見た目調整メニューは復活させていない
* Firebase / Firestore / Storage / Stripe / Cloud Run / 家族共有 / 保存処理は変更なし
* JavaScript構文チェック済み

## v313

* Minecraftの「見た目とサイズを調整」内にあった「現在の見え方」ミニプレビューを削除
* 既存の「マイクラでの見え方」プレビューへ表示を統合
* 調整中もプレビューを確認しやすいよう、プレビュー部分を上部に固定表示するレイアウトへ整理
* iPhone幅でプレビューが画面を占有しすぎないよう高さと余白を調整
* モブ風作品 β は引き続き公開UIから非表示
* 詳細な見た目調整メニューは復活させていない
* Firebase / Firestore / Storage / Stripe / Cloud Run / 家族共有 / 保存処理は変更なし
* JavaScript構文チェック済み

## v312

* Minecraftの「見た目とサイズを調整」内のミニプレビューを固定表示化
* 下のオプションを変更している時でも現在の見え方を確認しやすくした
* ミニプレビューをiPhone幅でも邪魔になりにくいサイズへ調整
* モブ風作品 β は引き続き公開UIから非表示
* 詳細な見た目調整メニューは復活させていない
* Firebase / Firestore / Storage / Stripe / Cloud Run / 家族共有 / 保存処理は変更なし
* JavaScript構文チェック済み

## v311

* Minecraftの「見た目とサイズを調整」内にミニプレビューを追加
* 設定変更後の見た目を、スクロールで上の大きなプレビューへ戻らず確認しやすくした
* 壁画サイズ、額縁デザイン、色・雰囲気、作品タイプ調整は維持
* モブ風作品 β は引き続き公開UIから非表示
* Firebase / Firestore / Storage / Stripe / Cloud Run / 家族共有 / 保存処理は変更なし
* JavaScript構文チェック済み

## v310

* Minecraftの「見た目とサイズを調整」と「詳細な見た目調整」を統合
* 「詳細な見た目調整を開く」を公開UIから削除
* 壁画サイズ、額縁デザイン、色・雰囲気、作品タイプを1か所に整理
* モブ風作品 β は引き続き公開UIから非表示
* Firebase / Firestore / Storage / Stripe / Cloud Run / 家族共有 / 保存処理は変更なし
* JavaScript構文チェック済み

## v309

* Minecraft保存/共有ボタンの文言を短くし、ボタン内に「プレミアム」「壁画用」を入れない公開向けUIに整理
* 「見た目とサイズを調整」を保存/共有ボタンより上へ移動し、壁画サイズと額縁デザイン5種類を見つけやすくした
* 手順案内を下方へ整理し、初期表示は折りたたみのコンパクトな案内に変更
* プレミアム会員には「無料で試せること / プレミアムでできること」の案内を表示しないようにした
* モブ風作品 β は引き続き公開UIから非表示
* Firebase / Firestore / Storage / Stripe / Cloud Run / 家族共有 / 保存処理は変更なし
* JavaScript構文チェック済み

## v308

* サービス公開に向けて「モブ風作品 β」を公開UIから非表示化
* Minecraft機能は壁画用中心に整理
* 壁画サイズ・額縁デザイン5種類は維持
* モブ風作品 β のロジックは大きく削除せず、将来復活しやすい形を維持
* Firebase / Firestore / Storage / Stripe / Cloud Run / 家族共有 / 保存処理は変更なし
* JavaScript構文チェック済み

## v307

* Minecraft向け額縁デザインを5種類（シンプル木枠、ナチュラル木目、白い美術館風、ダークブラウン、カラフルポップ）から選べるようにした
* デフォルトはシンプル木枠のまま、壁画/展示系のプレビューと `.mcaddon` の額縁テクスチャに反映
* モブ風作品 β のロジックは変更なし
* Firebase / Firestore / Storage / Stripe / Cloud Run / 家族共有 / 保存処理は変更なし
* JavaScript構文チェック済み

## v306

* 複数メディア作品の MEDIA PREVIEW で、前後ボタンから画像/PDF/メディアを切り替えできるように改善
* プレビュー画面に現在位置表示（例: `1 / 4`）を追加
* 1枚作品では前後ボタンと枚数表示を出さず、PDFプレビューや既存の拡大表示導線の挙動を維持
* Firebase / Firestore / Storage / Auth / Analytics 設定、Stripe、Cloud Run、Minecraft生成ロジックは変更なし
* JavaScript構文チェック済み

## v305

* README.md のMinecraft関連文言を現行UI・運用方針に合わせて整理
* Minecraft機能をメイン機能ではなく、作品を楽しむ追加の楽しみ方として扱う方針を明確化
* 「立体展示用」は復活させていない
* アプリ本体 `index.html` は変更なし
* 画面表示バージョン、Analytics `app_version`、Minecraft `.mcaddon` 内の v301 表記は変更なし

## v304

* GitHub管理上に残っていた古いバックアップHTML `index-backup.html` を削除した意図を記録
* 本番公開対象は `public/` であり、`index-backup.html` を `public/` に入れない運用を維持
* Firebase Hosting では `/index-backup.html` を `/` へ301リダイレクトする設定を維持
* アプリ本体 `index.html` は変更なし
* 画面表示バージョン、Analytics `app_version`、Minecraft `.mcaddon` 内の v301 表記は変更なし

## v303

* Firebase Hosting / Firestore Rules / Storage Rules の設定ファイルとして `firebase.json` をGitHub管理に追加
* `firestore.rules` をGitHub管理に追加し、`familyInvites` は `get` のみ許可、`list` は禁止するRulesを明文化
* `storage.rules` をGitHub管理に追加し、画像/PDFと25MB未満の制限を含む現行本番相当のルールを管理対象化
* アプリ本体 `index.html` は変更なし。画面表示バージョン、Analytics `app_version`、Minecraft `.mcaddon` 内の v301 表記も変更なし

## v302

* 手動Firebase Hostingデプロイ手順書 `DEPLOY_CHECKLIST.md` を追加
* GitHub `main` 反映と Firebase Hosting 本番反映を分離し、PCで手動確認後にデプロイする運用チェックを整理
* アプリ本体 `index.html` は変更なし。画面表示バージョン、Analytics `app_version`、Minecraft `.mcaddon` 内の v301 表記も変更なし

## v301

* ログイン後ヘッダーから「使い方」ボタンを削除し、スマホ幅でロゴ表示が圧迫されにくいよう調整
* トップ画面の「使い方をかんたんに見る」導線と使い方モーダル本体は維持
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v301 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* Firebase / Firestore / Storage / Authentication / Analytics 設定、Stripe / Cloud Run URL、課金処理、Minecraft生成ロジック、登録なし利用の画像参照パスは変更なし
* JavaScript構文チェック済み

## v300

* スマホでも初めての使い方を確認しやすいよう、トップ画面とログイン後ヘッダーに控えめな「使い方」導線を追加
* 登録なし体験、Googleログイン、作品保存、家族共有、PDF/画像プレビュー、Minecraftを追加の楽しみ方として案内する短いガイドを追加
* v299 は `SECURITY_REVIEW.md` 追加のみでアプリ本体は v298 のままだったため、今回の `index.html` 更新で画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v300 に更新
* Firebase / Firestore / Storage / Authentication / Analytics 設定、Stripe / Cloud Run URL、課金処理、Minecraft生成ロジック、登録なし利用の画像参照パスは変更なし
* JavaScript構文チェック済み

## v299

* 海外アクセス・botアクセス・不正利用リスクの観点で、現在の構成を確認する `SECURITY_REVIEW.md` を追加
* Firebase Hosting / Firestore Rules / Storage Rules の設定ファイルがこのリポジトリ内に存在しないことを明記し、Firebase Consoleまたはデプロイ元での確認ポイントを整理
* 登録なし利用、Cloud Run / Stripe Checkout、GA4 / Firebase Console / Stripeで見るべき運用確認項目、App Checkの段階導入時の注意点を整理
* アプリ本体の `index.html`、Firebase / Firestore / Storage / Authentication / Analytics / Stripe 設定、Minecraft生成ロジック、登録なし利用の画像参照パスは変更なし

## v298

* スマホ幅でトップ画面の横はみ出しを抑え、ヒーロー文言・CTA・機能カードの余白とタップ領域を微調整
* 登録なし利用の案内・サンプルカード・ボタンがiPhone幅でも読みやすく押しやすいよう、CSS中心で微調整
* 画像/PDFプレビュー画面の閉じるボタン、表示エリア、PDFフォールバック文言をスマホで扱いやすいサイズに調整
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v298 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* Firebase / Firestore / Storage / Authentication / Analytics / Stripe 設定、Minecraft生成ロジック、登録なし利用の画像参照パスは変更なし
* JavaScript構文チェック済み

## v297

* スマホ用ヒーロー見出しを短い専用コピーに出し分け、意図した位置で改行されるよう調整
* スマホ表示時にトップ画面のヒーロー見出しが右側に見切れないよう、見出しサイズと折り返し指定を調整
* トップ画面のロゴ・タグ、補足文、機能紹介カード、ログイン導線に `min-w-0` / `max-w-full` / 折り返し指定を追加し、横スクロールを抑制
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v297 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* Firebase / Firestore / Storage / Authentication / Analytics / Stripe 設定、Minecraft生成ロジック、登録なし利用の画像参照パスは変更なし
* JavaScript構文チェック済み

## v296

* 画像カードのタップ領域を明確にし、ギャラリー一覧・写真一覧・詳細画面・追加済みメディアから画像拡大プレビューを開ける導線を補強
* PDFカードのサムネイルURL判定を `thumbnail` / `thumbnailUrl` / `previewUrl` / `imageUrl` / `coverUrl` に拡張し、サムネイルがあるPDFは汎用PDFアイコンより優先して表示
* PDFサムネイルがない場合も「PDFを見る」「タップしてプレビュー」「PDFを開く」導線を維持し、登録なし利用サンプルPDFの既存サムネイル参照を維持
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v296 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* Firebase / Firestore / Storage / Authentication / Analytics / Stripe 設定、Minecraft生成ロジック、登録なし利用の画像参照パスは変更なし
* JavaScript構文チェック済み

## v295

* ギャラリーの画像カードをタップしたとき、既存のプレビュー画面で大きく確認できる導線を維持
* PDFカードをタップしたとき、1ページ目サムネイルがある場合はカードに表示し、プレビュー画面でPDFを確認できるよう改善
* 詳細画面の画像/PDFプレビューからも大きく確認できるよう、追加済みメディアのタップ導線を追加
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v295 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* Firebase / Firestore / Storage / Authentication / Analytics / Stripe 設定、Minecraft生成ロジック、ログイン導線は変更なし
* JavaScript構文チェック済み

## v294

* トップ画面のメインコピーを、子どもの作品・プリント・写真を成長記録として家族で残せるサービスだと分かる表現へ整理
* 登録なしのサンプル体験とGoogleログイン後の保存・家族共有の違いが伝わるよう、初回導線の文言を調整
* 機能紹介を「作品を残す」「プリントも整理」「家族で共有」「Minecraftで楽しむ」の4項目に整理し、Minecraftを追加の楽しみ方として案内
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v294 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* Firebase / Firestore / Storage / Authentication / Analytics / Stripe 設定、Minecraft生成ロジック、登録なし利用の画像参照パスは変更なし
* JavaScript構文チェック済み

## v293

* プレミアムプラン説明の保存容量・バックアップ表現を、過剰保証を避けつつ価値が伝わる文言へ調整
* 無料プランはCSV一覧、プレミアムはCSV + 写真一括バックアップ / ZIP出力と分かる説明に整理
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v293 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* Firebase / Firestore / Storage / Authentication / Analytics / Stripe 設定、Minecraft生成ロジック、登録なし利用の画像参照パスは変更なし
* JavaScript構文チェック済み

## v292

* 利用規約に、退会時・サービス終了時の保存データの取扱いと、エクスポート・ダウンロード・バックアップに関する説明を追加
* プライバシーポリシーに、退会・サービス終了時の個人情報の削除または匿名化、決済記録・問い合わせ履歴・アクセスログ等の保管期間に関する説明を追加
* プレミアム説明の保存容量表現を、通常利用に十分な保存容量・たっぷり保存が伝わる文言へ調整
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v292 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* Firebase / Firestore / Storage / Authentication / Analytics / Stripe 設定、Minecraft生成ロジック、退会処理、家族共有、登録なし利用の画像参照パスは変更なし
* JavaScript構文チェック済み

## v291

* 登録なし利用（ゲスト体験）バナーを、サンプル作品で試せることと保存・家族共有はログイン後に使えることが自然に伝わる文言へ調整
* ゲスト体験画面に「登録なしで試せること」「ログインするとできること」のコンパクトな説明カードを追加し、Googleログインへの保存開始導線を分かりやすく改善
* サンプルカードの説明文と、ゲスト体験中に保存・共有できない操作時の案内文を短く前向きな表現に整理
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v291 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* Firebase / Firestore / Storage / Authentication / Analytics / Stripe 設定、Minecraft生成ロジック、ログイン後機能、家族共有は変更なし
* JavaScript構文チェック済み

## v290

* 登録なし利用（ゲスト体験）のサンプルカードで参照していた画像拡張子を、Firebase Hosting上の実ファイルに合わせて `.png` へ修正
* PDFカードのサムネイル参照を `kindergarten-notice-page1.png` に修正し、正常時は汎用PDFアイコンではなくおたより画像が表示されるよう調整
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v290 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* Firebase / Firestore / Storage / Authentication / Analytics / Stripe 設定、Minecraft生成ロジック、ログイン後機能、家族共有は変更なし
* JavaScript構文チェック済み

## v289

* 登録なし利用（ゲスト体験）のサンプルデータを、子どもの絵・テスト・おたよりPDF・工作・季節制作・算数プリントの6件に差し替え
* ゲスト体験のサンプルカードでローカル静的ファイルの実画像を参照し、PDFは1ページ目サムネイル画像を表示できるよう調整
* ゲスト体験の保存不可・共有不可導線、ログイン後の通常保存、Firebase / Firestore / Storage / Authentication / Analytics / Stripe 設定、Minecraft生成ロジックは変更なし
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v289 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* JavaScript構文チェック済み

## v288

* Stripe Checkout Session作成APIへ送信するpayloadの戻り先URLを本番URL `https://kodomocapsule.com/` に統一
* `success_url` / `cancel_url` と互換用の `successUrl` / `cancelUrl` に同じ本番URLを入れ、Cloud Functions側の受け取りキー差異でも古いGitHub Pages URLへ戻らないよう修正
* Stripe Price ID、Checkout URL、Cloud Functions名、Firebase設定、既存のプレミアム判定・登録導線は変更なし
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v288 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* JavaScript構文チェック済み

## v287

* Stripe決済後の戻り先URLを本番URL `https://kodomocapsule.com/` に固定し、古いGitHub Pagesパスへ戻らないよう修正
* 決済成功後の `session_id` と既存の `family_id` 付与を維持し、プレミアム反映確認の既存処理を壊さないよう調整
* Stripe Price ID、Checkout URL、Cloud Functions名、Firebase設定、既存のプレミアム判定・登録導線は変更なし
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v287 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* JavaScript構文チェック済み

## v286

* Minecraft `.mcaddon` 保存・共有のプレミアム案内で、alert のOK後に既存のプレミアムプラン導線へ確実に進むよう修正
* Minecraft出力画面を閉じてから既存のプラン画面へ切り替えることで、元のMinecraft出力画面へ戻るだけになる挙動を防止
* 既存の `isPremiumUser` 判定を維持し、プレミアムユーザーの `.mcaddon` 保存・共有処理は従来どおり維持
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v286 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* JavaScript構文チェック済み

## v285

* プレミアムプラン画面に、Minecraft壁画保存をプレミアム機能として分かりやすく伝える価値説明を追加
* 作品を `.mcaddon` として保存し、Minecraftの壁に飾って家族だけの作品ギャラリーを作れることを、既存の登録導線を維持したまま案内
* 無料でもプレビューでき、プレミアムで `.mcaddon` 保存できる既存方針と、モブ風作品 βのおためし機能の案内を維持
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v285 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* JavaScript構文チェック済み

## v284

* Minecraft `.mcaddon` 保存・共有前のプレミアム案内から、既存のプレミアムプラン導線へ進む次アクションを分かりやすく調整
* 無料でもプレビューで仕上がり確認でき、プレミアムでは `.mcaddon` 保存後にMinecraftで開いて作品を飾れることが分かる文言に整理
* 既存の `isPremiumUser` 判定と保存実行関数側のガードを維持し、プレミアムユーザーの保存・共有処理は従来どおり維持
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v284 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* JavaScript構文チェック済み

## v283

* Minecraft `.mcaddon` 保存・共有前のプレミアム案内を、無料でもプレビュー確認できることとプレミアムで保存してMinecraftに飾れることが分かる文言に調整
* 保存・共有ボタン周辺の文言を、既存導線を維持したまま商用向けに分かりやすく整理
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v283 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* JavaScript構文チェック済み

## v282

* 既存の `isPremiumUser` 判定とプレミアム案内導線を使い、Minecraft `.mcaddon` 保存・共有の実行前にプレミアム確認を追加
* 無料ユーザーでもMinecraft出力画面のプレビュー、壁画サイズ選択、モブ風作品 βの設定、「見た目とサイズを調整」は使える方針を維持
* 保存ボタン周辺の文言を、プレミアムで `.mcaddon` を保存・共有する導線として整理
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v282 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* JavaScript構文チェック済み

## v281

* Minecraft出力画面に、無料でプレビューできることとプレミアムで .mcaddon 保存を便利に使えることの短い説明を追加
* 壁画用を、サイズを選んでMinecraftの壁に作品ギャラリーを作れるプレミアム価値のある正式機能として案内
* モブ風作品 βを、作品の雰囲気をもとにしたプレミアム向けβのおためし機能として整理
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version・option seed を v281 に更新し、Minecraftアイテム表示名にバージョンを含めない方針を維持
* JavaScript構文チェック済み

## v280

* Minecraft出力画面に、壁画用の保存後手順と `.mcaddon` の短い説明を追加
* iPhone / iPad / PCで保存後にMinecraftで開き、ワールド設定でパックを有効化して壁に飾る流れを整理
* 壁画用を正式機能・作品ギャラリーとして案内し、モブ風作品 βのおためし説明方針を維持
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version を v280 に更新
* JavaScript構文チェック済み

## v279

* Minecraftアイテム表示名・ホットバー・インベントリのツールチップに v279 などのバージョン表記が入らないよう、アイテム名と翻訳文字列を防御的に整形
* パック名・説明文・manifest version・option seed には v279 を反映し、検証用のバージョン表記を維持
* Minecraft出力画面の設定導線を「見た目とサイズを調整」に変更し、壁画サイズや見た目を調整できることが分かる説明に調整
* JavaScript構文チェック済み

## v278

* Minecraft出力画面で、壁画用を正式機能として分かりやすい表示・説明に整理
* モブ風作品にβ表記を追加し、作品の雰囲気をもとにした小さな置物のおためし機能として説明を調整
* 画面表示・Analytics・`.mcaddon` 内のパック名・説明文・manifest version を v278 に更新
* Minecraftアイテム表示名にはバージョン表記を含めない方針を維持
* JavaScript構文チェック済み

## v277

* Minecraftアイテム表示名から v277 などのバージョン表記を外し、作品タイトル・出力形式・サイズ情報を優先するよう調整
* 壁画用では、おまかせで解決された実サイズを引き続き「作品タイトル 壁画 サイズ」の形式で表示
* モブ風作品では、細かさ・展示サイズ・テンプレートを引き続き「作品タイトル モブ 細かさ 展示サイズ テンプレート」の形式で表示
* パック名・説明文・manifest version・option seed などの検証用バージョン情報は v277 として維持
* JavaScript構文チェック済み

## v276

* Minecraftアイテム表示名に、作品タイトル・出力形式・サイズ・v276を含めるよう改善
* 壁画用では、おまかせで解決された 1×1 / 2×2 / 3×3 / 4×4 などの実サイズがアイテム名で分かるよう調整
* モブ風作品では、24×24 / 32×32 などの細かさ、展示サイズ、縦長 / 箱型テンプレートがアイテム名で分かるよう調整
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v276 に更新
* JavaScript構文チェック済み

## v275

* 壁画サイズに「大きめ正方形 3×3」と「特大正方形 4×4」を追加
* 3×3 / 4×4 を壁画サイズUI、プレビュー、`.mcaddon` 実物ジオメトリ、表示名・説明文、option seed に反映
* 正方形に近い画像のおまかせ選択で、解像度に応じて 3×3 / 4×4 も候補にできるよう調整
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v275 に更新
* JavaScript構文チェック済み

## v274

* 壁画用の 1×1 / 1×2 / 2×1 / 2×2 / 2×3 / 3×2 / 4×3 が、Minecraft内の実物ジオメトリ幅・高さへ反映されるよう修正
* 壁画用エンティティの表示範囲と当たり判定を壁画サイズに追従させ、4×3 が明らかに大きい横長壁画として見えるよう調整
* v273で追加した壁画サイズUIと option seed 反映を維持し、画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v274 に更新
* JavaScript構文チェック済み

## v273

* モブ風作品の縦長タイプ / 箱型タイプで、写真貼り付けよりもシルエット・主要色・箱パーツ構成が分かりやすい比率へ調整
* 壁画用に「壁画サイズ」を追加し、おまかせ / 1×1 / 1×2 / 2×1 / 2×2 / 2×3 / 3×2 / 4×3 を選べるように変更
* 壁画サイズをプレビュー、`.mcaddon` ジオメトリ、表示名・説明文、重複回避用 option seed に反映
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v273 に更新
* JavaScript構文チェック済み

## v272

* モブ風作品に、写真の縦横比や横・上写真の色分布から縦長タイプ / 箱型タイプを自動判定する簡易テンプレート判定を追加
* 縦長タイプは帽子・頭・縦長胴体・薄い土台の既存方針を維持し、箱型タイプは頭・胴体に小さな腕・足パーツを加える形状へ分岐
* プレビューと `.mcaddon` 実物ジオメトリで同じテンプレート判定を使い、正面・横・上写真の面別活用を維持
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v272 に更新
* JavaScript構文チェック済み

## v271

* モブ風作品で正面写真を前面、横写真を側面、上写真を上面へ使い分けるテクスチャ生成に調整
* 横写真・上写真にも簡易トリミングと余白色置き換えを適用し、側面・上面は写真と代表色を控えめに混ぜるよう改善
* 背面は写真を無理に貼らず、パーツ代表色ベースの自然な塗りを維持
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v271 に更新
* JavaScript構文チェック済み

## v270

* モブ風作品で頭・胴体・帽子の白い余白面が目立ちにくいよう、余白色を各パーツの代表色で置き換える処理を追加
* `.mcaddon` の側面・背面・上下に、帽子・頭・胴体・土台それぞれの代表色スウォッチを使うよう調整
* モブ風作品の頭・胴体・帽子を少し細め、正面写真の中心部分が主役に見える比率へ調整
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v270 に更新
* JavaScript構文チェック済み

## v269

* モブ風作品で正面写真の白い余白や背景が大きく残りにくいよう、中央寄せの簡易トリミング範囲を追加
* 帽子・頭・胴体・土台へ貼る写真領域を共通のトリミング範囲から分け、プレビューと `.mcaddon` 実物の貼り付け方針を統一
* 側面・背面は代表色ベースを維持し、v268 の検証用アドオン重複回避仕様を v269 として継続
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v269 に更新
* JavaScript構文チェック済み

## v268

* 検証用アドオンで、UUID / identifier / geometry identifier の seed に出力オプション情報を含めるよう変更
* 同じ作品でも、表情の細かさ・展示サイズ・出力形式などが違う場合は別パック・別アイテムとしてインポートしやすい生成方式へ改善
* 同じ作品・同じ出力形式・同じオプションでは UUID / identifier / version が決定的に同じになるよう維持
* `.mcaddon` 内の表示名・説明文に v268、出力形式、表情の細かさ、展示サイズが分かる情報を追加
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v268 に更新
* JavaScript構文チェック済み

## v267

* モブ風作品を、背面支柱なしの帽子・頭・胴体・薄い土台で構成するシンプルなモブ像テンプレートへ調整
* `.mcaddon` のモブ風ジオメトリで、側面・背面への写真テクスチャ回り込みを抑え、代表色ベースで見えるよう調整
* 同じ作品・同じ出力形式では UUID / identifier が安定し、壁画用とモブ風作品で衝突しない生成方式へ変更
* manifest version を v267 と出力オプションの組み合わせから決定的に生成し、依存関係の version と整合させるよう改善
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v267 に更新
* JavaScript構文チェック済み

## v266

* モブ風作品のプレビューで、頭・帽子・胴体・土台を隙間と奥行き差のあるパーツ型に調整
* `.mcaddon` のモブ風ジオメトリで、各パーツの側面にも正面写真の各領域を使い、白い背面箱に見えにくい形へ調整
* 必要最小限の細い背面支柱だけを残し、展示サイズごとのスケール追従は維持
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v266 に更新
* JavaScript構文チェック済み

## v265

* モブ風作品のプレビューで、土台・屋根・外枠に見える張り出しを控えめに調整
* `.mcaddon` のモブ風ジオメトリでも、台座・支え・屋根を小さくし、頭・帽子・胴体が目立つ比率へ調整
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v265 に更新
* JavaScript構文チェック済み

## v264

* ログイン前画面が「読み込み中...」で止まる原因になっていた `drawMinecraftVoxelExhibitPreview` の重複定義を解消
* v263 のモブ風作品プレビュー描画を残し、旧ボクセル風立体プレビューの不要な重複関数を削除
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v264 に更新
* JavaScript構文チェック済み

## v263

* ボクセル風立体を廃止し、出力形式を「壁画用 / モブ風作品」の2択に変更
* モブ風作品のプレビューを、頭・帽子・胴体・土台に分かれた簡易3Dモデル表示へ変更
* `.mcaddon` の立体作品生成を、板状レリーフではなく奥行きのあるモブ風テンプレート形状へ変更
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v263 に更新
* JavaScript構文チェック済み

## v262

* Minecraft ボクセル風立体のかんたん設定に「展示サイズ」を追加
* 展示サイズを「標準 / 大きめ / 特大」から選べるようにし、初期値を「大きめ」に設定
* プレビュー表示と `.mcaddon` の実物ジオメトリ生成に同じ展示サイズを反映
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v262 に更新
* JavaScript構文チェック済み

## v261

* Minecraft ボクセル風立体で、正面写真の顔・線・絵柄が見やすいようにプレビューの描画順を調整
* 側面・上面・影・ハイライトの強さを控えめにし、正面の色面へ重なりにくく調整
* プレビューと `.mcaddon` の奥行き補正を共通化し、正面視認性を優先する見え方へ調整
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v261 に更新
* JavaScript構文チェック済み

## v260

* Minecraft ボクセル風立体で、横写真の色味を側面へ反映しやすく調整
* Minecraft ボクセル風立体で、上写真の色味を上面へ反映しやすく調整
* 白背景や机色が側面・上面に強く出すぎないよう、写真の色抽出を補正
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v260 に更新
* JavaScript構文チェック済み

## v259

* Minecraft ボクセル風立体のプレビューで、厚み計算を `.mcaddon` の実物形状と共通化
* プレビューの影・側面・上面の強調を抑え、実際のボクセル形状に近い見え方へ調整
* 画面表示・Analytics・`.mcaddon` 内表示名のバージョンを v259 に更新
* JavaScript構文チェック済み

## v258

* Minecraft ボクセル風立体で、作品本体の輪郭や濃い線を残しやすく調整
* 背景カット時に顔・飾り・濃い線・色の強い部分が欠けにくいよう補正
* プレビューと `.mcaddon` の両方で同じシルエット補正を使用
* JavaScript構文チェック済み

## v257

* 縦長の立体作品を自動判定し、横幅を少し補正
* 細い板のように見えにくいよう、プレビューと `.mcaddon` 形状の両方に反映
* 縦長作品では背面の支えと台座を少し強めるよう調整
* JavaScript構文チェック済み

## v256

* 背景カットにおすすめ表示を追加
* 写真の明るい余白・背景量を見て「やさしめ / 標準 / 強め」のおすすめを表示
* 自動で勝手に切り替えず、現在の設定とおすすめを分かるように表示
* JavaScript構文チェック済み

## v255

* 立体作品のMinecraftプレビューに「きれいに作る撮影のコツ」を追加
* 背景・明るさ・中央配置・正面/横/上写真の撮り方を案内
* 立体作品の時だけ表示されるよう調整
* JavaScript構文チェック済み

## v254

* 「ボクセル設定を開く」を削除
* 「ボクセルの細かさ / 背景カット / 立体感」を「かんたん設定」に統合
* ボクセル風立体の時だけ、かんたん設定内に表示されるよう調整
* JavaScript構文チェック済み

## v253

* 「ボクセルの細かさ / 背景カット / 立体感」をトグルメニュー化
* 「かんたん設定」をトグルメニュー化
* JavaScript構文チェック済み

## v252

* 「ボクセルの細かさ」「背景カット」「立体感」を「マイクラでの見え方」の下へ移動
* 表示順を整理
* JavaScript構文チェック済み

## v251

* PC操作時は「大人向けのくわしい手順」を非表示化
* 不要な説明カードを非表示化
* JavaScript構文チェック済み
