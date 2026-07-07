# コドモカプセル

子どもの作品・写真・記録を保存し、家族で振り返るためのWebアプリです。
単一の `index.html` を中心に構成されています。

## 開発方針

* GitHub Pagesで公開する
* HTML / CSS / JavaScriptのみで動作する
* 既存機能を壊さないことを最優先にする
* Firebase / Firestore / Storage / Authentication / Analytics / Stripe 関連の仕様は、明示的な依頼がない限り変更しない
* 大きなリファクタリングは行わず、小さな差分で安全に改修する
* 変更後は必ずJavaScript構文チェックを行う
* Firebase Hosting の本番反映は自動化せず、手動デプロイ手順は `DEPLOY_CHECKLIST.md` を参照する

## 重要な既存機能

* 子どもの作品・写真・記録の登録
* ギャラリー表示
* 画像 / PDFプレビュー
* 家族共有
* Minecraft Bedrock Edition向け `.mcaddon` 生成
* 作品をMinecraftの壁画として楽しむ追加機能
* iPhone / iPad / PCでの操作

## Minecraft機能の注意点

* Minecraft機能はメイン機能ではなく、作品を楽しむ追加の楽しみ方として扱う
* Minecraft機能は、作品をMinecraftの壁画として楽しむ追加機能として公開UIを整理する
* Minecraftアイテム表示名にはバージョン番号を含めない
* iPhone / iPad の `.mcaddon` ダウンロード・共有導線は壊さない
* Minecraft生成ロジックは、明示的な依頼がない限り変更しない

## バージョン管理

* 画面上のバージョン表記を更新する
* Analytics の `app_version` も同じバージョンに更新する
* 1回の改修につき、バージョンを1つだけ上げる

## Codexへの依頼方針

Codexには、一度に大きな改修をさせず、1つの目的に絞った小さな変更を依頼する。
変更後は以下を報告すること。

* 変更内容
* 変更した主な関数・UI
* 影響範囲
* JS構文チェック結果
* 実機確認ポイント
