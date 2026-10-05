# AIパズル販売スタートガイド（Instagramリール特典ページ）

> 設計の共通原則（基本原則・資産価値の原則・自律解決の原則）は `~/.claude/CLAUDE.md` に従う。

## プロジェクト設定

技術スタック:
  frontend: HTML5 / CSS3 / Vanilla JavaScript（ビルド工程なし・フレームワーク不使用）
  backend: なし
  database: なし
  hosting: GitHub Pages（静的ファイル配信のみ）

ビルド・サーバーが不要な完全な静的サイト。`index.html` を直接開く、または
`python3 -m http.server <port>` を1つだけ起動して確認する。ポートのランダム生成・バックエンドポートは不要。

## 環境変数

使用しない（APIキー・DB接続情報が一切不要）。`.env` 系ファイルは作成しない。

## ファイル構成の原則

兄弟リポジトリ（`digital-planner-tokuten` 等）と同じフラット構成を維持する。

```text
index.html / style.css / script.js / README.md / assets/ / docs/
```

- **文章の単一の源は `index.html`**（5つのプロンプト本文もここ）。`content.js` / `config.js` は作らない
- **設定値の単一の源は `script.js` 先頭の定数**: `LINE_URL`（LINE登録URL・空ならボタン非表示）。OGPはクローラーがJSを実行しないため `index.html` の静的な meta タグで設定
- コピーボタンは、画面表示のプロンプトと同じテキストを取得する（別管理にしない＝欠落防止）
- 完了チェックの保存は localStorage（キー `puzzle:progress`）。使えない環境でも動くよう try/catch

## 命名規則

- ファイル: kebab-case / JS変数・関数: camelCase / 定数: UPPER_SNAKE_CASE / CSSクラス: BEM風

## 配色（変更しないこと。変える場合はユーザー確認）

大人ピンク×アイボリー系。青・紫・ネオン・派手なグラデーション不可。設計書のブラウン主体は不採用（2026-10-05 ユーザー指示）。

| 用途 | 変数 | 値 |
|---|---|---|
| 背景 | `--color-bg` | `#fdfaf7` |
| 淡いブラッシュピンク | `--color-bg-soft` | `#fbeeec` |
| メインピンク | `--color-primary` | `#d03f64` |
| 濃いピンク | `--color-primary-dark` | `#b02c52` |
| アクセント淡ピンク | `--color-accent-light` | `#f7dfe0` |
| メイン文字（濃茶） | `--color-text` | `#3d322f` |
| 補助文字 | `--color-text-muted` | `#8a7972` |
| ボーダー | `--color-border` | `#f0dfdc` |

## 内容の方針（必ず守る）

- 要件は `docs/requirements.md` が単一の源。内容を勝手に増やさない
- 確認できないPrintify/Etsyの仕様・料金・対応地域・規約は書かず「最新の公式情報を確認」。架空の画面名・販売実績・体験談を書かない
- CTAは「AIマネタイズの教科書」＋「AI収益化サポート会／個別相談」の標準構成を常時表示（CTA①＝STEP 2の後・軽量版、CTA②＝最下部・完全版＋画面下の常時表示ボタン）。LINE登録は強制しない。教科書の目次は添付画像 `assets/images/cta-textbook-contents.png`
- 「リスクゼロ」「必ず売れる」「誰でも稼げる」は使わない。「月5万」は目標の一例と明記
- OGP画像は設定しない（`twitter:card=summary`）

## 画像の扱い

`<img>` に `width` / `height` 属性を付けない。CSSで `aspect-ratio` + `object-fit: contain` + `height: auto`（Instagramアプリ内ブラウザでの縦引き伸ばし対策）。

## コード品質

- 関数: 100行以下 / ファイル: 700行以下 / 複雑度: 10以下 / 行長: 120文字
- 700行基準は `style.css` / `script.js` に適用。`index.html` は文章保持のため対象外

## 表示確認（納品前に必須）

Playwrightで実ビューポートを再現する（claude-in-chrome の `resize_window` はCSSビューポート幅が変わらず不可）。
確認項目は `docs/requirements.md` §4。

## 開発ルール

- デプロイはユーザーの明示的な承認を得てから実行する
- 許可されたドキュメントのみ作成可能: `README.md` / `docs/requirements.md` / `docs/SCOPE_PROGRESS.md`。それ以外はユーザー許諾が必要
- 実装済みの記載は積極的に削除する
- Gitのコミット著者は mion-ai-mama の noreply（本名・個人メールでコミットしない）

## Playwright

スクリーンショット保存先: /tmp/bluelamp-screenshots/
