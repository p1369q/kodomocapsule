# AGENTS.md

このリポジトリは「コドモカプセル」という単一HTML Webアプリです。
Codex / coding agent は、このファイルの内容を必ず守って作業してください。

## 最重要ルール

* 既存機能を壊さないことを最優先にする。
* 変更は小さな差分に限定する。
* 1回のタスクでは、1つの目的だけを実装する。
* 大きなリファクタリング、全面書き換え、構造変更は行わない。
* 指示されていない機能追加やUI変更は行わない。
* 不明点がある場合は、推測で大きく変更せず、最小限の安全な変更に留める。

## 編集対象

原則として編集対象は以下のみ。

* `index.html`
* `CHANGELOG.md`

以下のファイルは、明示的な指示がない限り変更しない。

* `index-backup.html`
* `README.md`
* 画像ファイル
* 設定ファイル
* GitHub Pages関連設定

## Pull Request運用

* 直接 `main` ブランチに反映しない。
* 作業ブランチを作成し、Pull Request として提案する。
* Pull Request には、変更内容・影響範囲・確認方法を明記する。
* 変更ファイルが多くなりすぎた場合は、作業を止めて理由を報告する。

## バージョン管理

* 1回の改修につき、バージョンを1つだけ上げる。
* 画面上のバージョン表記を更新する。
* Analytics の `app_version` も同じバージョンに更新する。
* Minecraft `.mcaddon` 内にバージョン表記がある場合は、必要に応じて同じバージョンに揃える。
* `CHANGELOG.md` の先頭に新しいバージョンの変更内容を追記する。

例：

```md
## v259

- 変更内容1
- 変更内容2
- JavaScript構文チェック済み
```

## 触ってはいけない領域

明示的な依頼がない限り、以下の仕様は変更しない。

* Firebase Authentication
* Firestore
* Firebase Storage
* Firebase Analytics
* Stripe
* Cloud Functions
* セキュリティルール
* ログイン導線
* 家族共有・権限管理
* プレミアムプラン・課金関連
* アカウント削除関連

これらのコードに触る必要がある場合は、変更前に理由を明記する。

## Minecraft機能の注意点

* 「立体展示用」は過去に削除済みのため、復活させない。
* 立体作品の出力形式は、基本的に「壁画用」と「ボクセル風立体」の2つを維持する。
* iPhone / iPad / PC の `.mcaddon` ダウンロード・共有導線を不用意に変更しない。
* 「① この端末で実行」はダウンロード導線として維持する。
* 「② アドオンを共有」は共有導線として維持し、自動ダウンロードに戻さない。
* プレビューと `.mcaddon` の実物形状ができるだけ一致するようにする。
* プレビュー側だけ、または `.mcaddon` 側だけに補正を入れない。可能な限り共通処理を使う。
* 既存の「ボクセルの細かさ」「背景カット」「立体感」の操作を壊さない。

## UI変更の方針

* 子どもや保護者が迷わない、シンプルな文言にする。
* 既存の見た目や配置を大きく変えない。
* 不要な説明を増やしすぎない。
* PC / iPhone / iPad の表示崩れに注意する。
* 既存IDや既存関数名は、必要がない限り変更しない。

## JavaScript構文チェック

変更後は必ず JavaScript 構文チェックを行う。

`index.html` をそのまま `node --check` しない。
HTML内の inline script のみを抽出してチェックする。

除外する script：

* `src` 付き script
* `type="importmap"`
* `application/ld+json`
* `application/json`

チェック例：

```bash
python3 - <<'PY'
from html.parser import HTMLParser
from pathlib import Path

class P(HTMLParser):
    def __init__(self):
        super().__init__()
        self.ins = False
        self.skip = False
        self.parts = []
        self.cur = []

    def handle_starttag(self, tag, attrs):
        if tag.lower() == "script":
            a = dict(attrs)
            t = (a.get("type") or "").lower()
            self.ins = True
            self.skip = ("src" in a) or (t == "importmap") or ("ld+json" in t) or (t == "application/json")
            self.cur = []

    def handle_endtag(self, tag):
        if tag.lower() == "script" and self.ins:
            if not self.skip:
                self.parts.append("".join(self.cur))
            self.ins = False
            self.skip = False
            self.cur = []

    def handle_data(self, data):
        if self.ins and not self.skip:
            self.cur.append(data)

html = Path("index.html").read_text(encoding="utf-8")
p = P()
p.feed(html)
Path("/tmp/kodomocapsule-inline.js").write_text("\n;\n".join(p.parts), encoding="utf-8")
print(len(p.parts), "inline JavaScript scripts extracted")
PY

node --check /tmp/kodomocapsule-inline.js
git diff --check
```

## 完了時の報告内容

作業完了時は、必ず以下を報告する。

* Summary
* 変更したファイル
* 変更した主な関数・UI
* 影響範囲
* 触っていない重要領域
* JavaScript構文チェック結果
* PC / iPhone / iPad で確認すべきポイント

## 報告フォーマット

```md
## Summary

- 変更内容1
- 変更内容2

## Changed files

- index.html
- CHANGELOG.md

## Main changes

- 変更した関数やUI

## Not changed

- Firebase / Firestore / Storage / Authentication / Analytics / Stripe 関連は変更なし
- index-backup.html は変更なし
- 「立体展示用」は復活させていない

## Testing

- inline script 抽出後、node --check 実行済み
- git diff --check 実行済み

## Manual check points

- PCで表示確認
- iPhone / iPadで表示確認
- Minecraft `.mcaddon` のダウンロード確認
- Minecraftへのインポート確認
```

## 現在の重点開発領域

現在は、Minecraft Bedrock Edition向け `.mcaddon` 生成機能のうち、特に「ボクセル風立体」の品質改善を優先している。

優先テーマ：

* 背景カット精度の改善
* 作品本体のシルエット保持
* 細長い立体作品の見た目改善
* プレビューとMinecraft実物の差を減らす
* 横写真・上写真の反映強化
* iPhone / iPadでの導線維持

ただし、各タスクでは一度にすべてを実装せず、1つずつ安全に進めること。
