# 全日本学生釣魚連盟関東支部 公式サイト

本プロジェクトは、連盟の活動報告および情報発信の効率化を目的として設計・実装・納品までを行った、ブログ統合型の公式サイトです。

## プロジェクトの成果
* **運用の効率化:** 非エンジニアのメンバーでも、ブラウザから数クリックで活動報告やニュースを更新できるヘッドレスCMS（microCMS）を基盤としたシステムを構築しました。
* **活動の発信をより身近に:**「日々の活動報告や大会の成果をリアルタイムに共有したい」という団体の要望に基づき、記事投稿が容易なブログ型の構成を採用しました。

## 使用技術
* **Frontend:** Astro.js (高速な表示パフォーマンスとSEO最適化のため採用)
* **Styling:** Tailwind CSS / SCSS
* **CMS:** microCMS (APIベースのコンテンツ管理)

## 設計のポイント
* ページの大半が静的コンテンツであるためAstroを採用し、優れたユーザー体験を実現しています。
* UIを再利用可能なパーツとして切り出すことで、将来的なページ追加やデザイン変更が容易な構成にしています。
* Tailwind CSSに加え、複雑な指定にはSCSSを用いることで、コードの可読性とデザインの一貫性を両立させました。

## 補足事項
* 本リポジトリは、全日本学生釣魚連盟関東支部へ正式に納品した初期リリース版のソースコードを管理しています。
* コンテンツに関しては、納品時のシステム稼働確認用として用意したサンプルデータを掲載しています。

## 構成
```
public
├── assets
src
├── components
│   ├── Footer.astro
│   └── Header.astro
├── env.d.ts
├── layouts
│   └── Layout.astro
├── lib
│   └── microcms.ts
├── pages
│   └── index.astro
├── scss
│   ├── _variables.scss
│   └── styles.scss
astro.config.mjs
│
package.json
│
package-lock.json
│
tailwind.config.mjs
│
tsconfig.json
```
ディレクトリ構成は以上のようになっています。``/src/pages/index.astro``がサイトのTOPページに相当します。
フレームワークはAstro.js、CSSフレームワークはTailwind CSSを使用しています。TypeScriptを使用できるようにしています。CMSにはmicroCMSを使う想定です。<br />

### コーディングの仕方
#### 1. セットアップ
VSCodeでフォルダを開きターミナルで、``npm install``を実行し、node_modulesをインストールする。このコマンドを実行することで、package.jsonの記述をもとに必要なnode_modulesがインストールされ、AstroやTailwindが利用可能になる。package.jsonファイルにこのプロジェクトで使うパッケージが記述されているので、見てみると良い。
#### 2. 開発を始める
Astroで開発する際はローカルサーバーを立ち上げて実行画面を見ながら作業する。
VSCodeでフォルダを開きターミナルで、``npm run dev``を実行し、ブラウザのURLバーでlocalhost:4321にアクセスすると実行画面が開ける。まだ何も書かれていないので、最初は空白のはずである。
#### 3. TOPページのコーディングをする
``/src/pages/index.astro``がTOPページに相当するファイルです。
#### 4. 下層ページを作る
下層ページを作るときは``/src/pages/``配下に新しいディレクトリを作り、その中にindex.astroファイルを作って書くようにしてください。以下の例はaboutページを作る際の例です。
```
├── pages
│   └── index.astro
│   └── about
│       └── index.astro
``` 
#### 5. cssの書き方
SASSを使えるようにしています。``/src/scss/styles.scss``に基本的に書くようにしてください。SASSはCSSのように書くことができますが、SASSの記法を覚えるとより効率的に書けるので、[このドキュメント](https://zenn.dev/hinoshin/articles/b13c8181df9a93)を見て、活用してみてください。
