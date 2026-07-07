# 手動Firebase Hostingデプロイチェックリスト

## 目的

この手順書は、GitHub `main` へのマージと Firebase Hosting の本番反映を分離し、PCでの手動確認後に安全に本番へ出すための運用チェックリストです。

スマホ実機確認、Firebase / Stripe / Minecraft まわりの副作用確認を行ったうえで、Firebase Hosting 用の `public/` フォルダから手動でデプロイします。

## デプロイ前チェック

- GitHub `main` に目的のバージョンが反映済みであること
- `CHANGELOG.md` の先頭が対象バージョンであること
- GitHub 上の `index.html` の `environmentBadge` が対象バージョンであること
- ローカルPCの `public/index.html` を最新版に置き換えたこと
- `public/assets/` が残っていること
- `public/` に `index-backup.html` を入れないこと
- `public/` に不要な古いHTML、`.env`、秘密情報、メモファイルを入れないこと

## 推奨 public 構成

Firebase Hosting へデプロイする `public/` は、次のような最小構成を推奨します。

```text
public/
  assets/
  index.html
  ogp.png
```

## Firebase設定ファイルとRulesの運用

- `firebase.json` / `firestore.rules` / `storage.rules` はGitHub管理対象です。
- Rulesだけ更新する場合は、対象を明示して次のコマンドを使います。

```bash
firebase deploy --only firestore:rules
firebase deploy --only storage
```

- Hostingだけ更新する場合は、次のコマンドを使います。

```bash
firebase deploy --only hosting
```

- 誤って全体デプロイする前に、デプロイ対象が Hosting / Firestore Rules / Storage Rules のどれかを必ず確認します。

## デプロイコマンド

Firebase Hosting の本番反映は、PC上の Firebase Hosting 用フォルダで次のコマンドを実行します。

```bash
firebase deploy --only hosting
```

必要に応じて、対象バージョンが分かるコメントを付けてデプロイします。

```bash
firebase deploy --only hosting -m "Deploy vXXX"
```

## デプロイ後チェック

- https://kodomocapsule.com/ を開く
- 画面表示バージョンが対象バージョンであること
- スマホでトップ画面が崩れていないこと
- ログインできること
- 登録なし利用が開けること
- 画像/PDFプレビューが開けること
- Stripe / プレミアム表示に不要な変化がないこと
- Minecraft関連UIに古い文言が復活していないこと
- https://kodomocapsule.com/index-backup.html が表示されないこと

## トラブル時

- 本番表示が古い場合は、ブラウザキャッシュ、Firebase Hosting のデプロイ履歴、`public/index.html` の中身を確認すること
- v表示が違う場合は、デプロイ元の `public/index.html` が古い可能性が高いこと
- 重大な表示崩れがあれば、Firebase Hosting のリリース履歴からロールバックを検討すること
- Firebase Console 側の Rules や Cloud Run / Stripe 設定は、この手順書だけでは変更しないこと
