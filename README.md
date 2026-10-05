# AIで作る「オリジナルパズル販売」スタートガイド（Instagramリール特典ページ）

ビルド不要の静的サイト（HTML / CSS / JavaScript）です。

```text
index.html   ページ本体（文章・プロンプトはここが単一の源）
style.css    見た目（色は先頭の :root で変更）
script.js    コピー・完了チェック・固定ボタン（LINE_URL は先頭の定数）
assets/      CTAバナー・教科書の目次画像・favicon
docs/        要件定義書・進捗管理表
```

## ローカルで確認する

```bash
python3 -m http.server 8000
```

→ http://localhost:8000

## 公開する

GitHub の Settings → Pages で、ブランチ `main`・フォルダ `/ (root)` を選びます。公開URL: `https://mion-ai-mama.github.io/ai-puzzle-tokuten/`

## 内容について

Printify・Etsy等の仕様、料金、対応地域、規約は変わるため、ページ内には具体的な数値を載せていません。「月5万」は目標の一例で、収益を保証するものではありません。
