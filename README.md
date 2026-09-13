# 田崎昭作 公式参考サイト — GitHub Pagesへの公開手順

このフォルダには、完成済みの静的サイト（HTML/CSSのみ、ビルド不要）が入っています。
GitHub Pagesで公開するための手順は以下の通りです。

## 1. GitHubアカウントとリポジトリの準備

1. GitHub（https://github.com）のアカウントをまだ持っていなければ作成する（無料）。
2. 新しいリポジトリを作成する（例：`tasaki-shosaku`）。Publicに設定する（GitHub Pagesの無料利用にはPublicリポジトリが必要）。

## 2. ファイルのアップロード

このフォルダの中身（`index.html`、`biography.html`、`works.html`、`style.css`、`robots.txt`、`sitemap.xml`、`assets/`フォルダ〈favicon・OGP画像〉、`ja/`フォルダ、このREADME）を、作成したリポジトリのルートにそのままアップロードする。フォルダ構造（`assets/`、`ja/`のサブフォルダ）を崩さないこと。

- GitHubのWeb画面からドラッグ&ドロップでアップロードする方法が最も簡単です（「Add file」→「Upload files」）。
- 操作に慣れていれば、`git clone` してファイルをコピーし `git push` する方法でも構いません。

## 3. GitHub Pagesを有効化

1. リポジトリの「Settings」タブを開く。
2. 左メニューの「Pages」を選択。
3. 「Source」を「Deploy from a branch」、ブランチを「main」（フォルダは「/ (root)」）に設定して保存。
4. 数分後、`https://<ユーザー名>.github.io/<リポジトリ名>/` でサイトが公開される。

## 4. 独自ドメインの設定（任意・推奨）

1. お好きなドメイン（例：`tasaki-shosaku.com` や `.jp` ドメインなど）をドメインレジストラ（お名前.com、Squarespace Domains、Namecheap等）で取得する。取得・支払いはユーザー自身の操作が必要（Claudeは決済を代行できない）。
2. レジストラのDNS管理画面で、以下のレコードを追加する（GitHub公式ドキュメントで2026年時点も変更なしと確認済み）。
   - **アペックスドメイン**（例：`tasaki-shosaku.com` 本体）を使う場合：Aレコードを4つ、下記の値ですべて追加する。
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - **wwwサブドメイン**（`www.tasaki-shosaku.com`）も使う場合：CNAMEレコードを1つ追加し、値を `ttakt.github.io` にする。
   - 上記いずれか、または両方を設定する（両方設定して、後述のGitHub側で正規化するのが一般的）。
3. リポジトリの「Settings」→「Pages」の「Custom domain」欄に取得したドメインを入力して保存する。これによりリポジトリのルートに`CNAME`ファイルが自動生成され、数時間以内に無料のSSL証明書（HTTPS）も自動発行される。「Enforce HTTPS」にチェックが入っていることを確認する。
4. **【重要・忘れやすい】ドメインを切り替えたら、サイト内に埋め込まれた `https://ttakt.github.io/tasaki-shosaku/` という文字列を、新しいドメインにすべて置換する必要がある。** 対象は以下の6ファイル・2ファイル：
   - 6ページ（`index.html`／`biography.html`／`works.html`とその`ja/`版）内の `<link rel="canonical">`、`<link rel="alternate" hreflang="...">`、`og:url`、`og:image`、`twitter:image` の各URL
   - `sitemap.xml`内の全URL
   - これを忘れると、検索エンジンには「新ドメインのページ」と「github.ioの旧URL」が別ページとして扱われ、せっかくのSEO評価が分散してしまう。
5. Google Search Consoleに新しいドメインを別プロパティとして追加し、`sitemap.xml`を再送信する（ドメインが変わるとSearch Console上は別サイト扱いになるため、旧URLでのインデックス登録実績は自動的には引き継がれない）。

## バージョン管理について

このZIPの配布ファイル名には日付+時刻（日本時間、`_YYYYMMDD-HHMM`形式）を付けて運用しています。同じ日に複数回更新されることがあるため、日付だけでは版が特定できません。ファイル名は将来リネームされる可能性があるため、最終的な正は同梱の `CHANGELOG.md` です。更新するたびにそちらへ1行追記されます。

## 今後の拡張

- 作品画像（図録からの切り出し）を用意できたら、`works.html`の各行に `<img>` を追加する、または作品ごとの個別ページを増設する。
- 英語ページを増やす場合は、このフォルダ直下に追加し、`ja/`フォルダには日本語版を追加する、という対になる構成を保つと管理しやすい。
- データの更新は、`田崎昭作_経歴年表_作品目録_第三者ソース.xlsx`の内容が確定するたびに、このHTMLへ反映する運用を想定している。
