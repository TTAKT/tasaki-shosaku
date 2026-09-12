# 田崎昭作 公式参考サイト — GitHub Pagesへの公開手順

このフォルダには、完成済みの静的サイト（HTML/CSSのみ、ビルド不要）が入っています。
GitHub Pagesで公開するための手順は以下の通りです。

## 1. GitHubアカウントとリポジトリの準備

1. GitHub（https://github.com）のアカウントをまだ持っていなければ作成する（無料）。
2. 新しいリポジトリを作成する（例：`tasaki-shosaku`）。Publicに設定する（GitHub Pagesの無料利用にはPublicリポジトリが必要）。

## 2. ファイルのアップロード

このフォルダの中身（`index.html`、`biography.html`、`works.html`、`style.css`、`ja/`フォルダ、このREADME）を、作成したリポジトリのルートにそのままアップロードする。

- GitHubのWeb画面からドラッグ&ドロップでアップロードする方法が最も簡単です（「Add file」→「Upload files」）。
- 操作に慣れていれば、`git clone` してファイルをコピーし `git push` する方法でも構いません。

## 3. GitHub Pagesを有効化

1. リポジトリの「Settings」タブを開く。
2. 左メニューの「Pages」を選択。
3. 「Source」を「Deploy from a branch」、ブランチを「main」（フォルダは「/ (root)」）に設定して保存。
4. 数分後、`https://<ユーザー名>.github.io/<リポジトリ名>/` でサイトが公開される。

## 4. 独自ドメインの設定（任意・推奨）

1. お好きなドメイン（例：`tasaki-shosaku.com` や `.jp` ドメインなど）をドメイン registrar（Google Domains後継のSquarespace、お名前.com等）で取得する。
2. ドメインのDNS設定で、GitHub Pages向けのAレコード／CNAMEレコードを追加する（GitHub公式ドキュメント「Managing a custom domain for your GitHub Pages site」の手順に従う）。
3. リポジトリの「Settings」→「Pages」の「Custom domain」欄に取得したドメインを入力して保存すると、自動的にSSL証明書も発行される。

## 今後の拡張

- 作品画像（図録からの切り出し）を用意できたら、`works.html`の各行に `<img>` を追加する、または作品ごとの個別ページを増設する。
- 英語ページを増やす場合は、このフォルダ直下に追加し、`ja/`フォルダには日本語版を追加する、という対になる構成を保つと管理しやすい。
- データの更新は、`田崎昭作_経歴年表_作品目録_第三者ソース.xlsx`の内容が確定するたびに、このHTMLへ反映する運用を想定している。
