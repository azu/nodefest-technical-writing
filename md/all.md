# 技術文書をソフトウェア開発する話

技術文書の自動テスト、開発プロセスについて

----

# 自己紹介

![アイコン, left](https://github.com/azu.png)

- Name : **azu**
- Twitter : @[azu_re](https://twitter.com/azu_re)
- Website: [Web scratch], [JSer.info]

[Web scratch]: http://efcl.info/ "Web scratch"
[JSer.info]: http://jser.info/ "JSer.info"

----

# 目的

- 技術文書を書くのはもっと身近ものとなっている事を知る
- ブログの延長線上としてのステップ
- 技術文書をテストする

----

# Why techinical writing?

- 文章だと小説とかも含まれてるのでやり方が異なりそう
- 技術文書だとセマンティックがはっきりしてるのでとりかかりやすい
    - 「技術書の英語は読みやすい」とかそういうのに近い
- なのでまずは身近な技術文書からやりましょう

----

# アジェンダ

- 技術書を書くモチベーション
    - ブログは書くけど技術書みたいな長いものは書けない
    - 途中で放置された文章
    - 完成が見えずに放置されたソフトウェア
    - とりあえず動くようにして進めていく
    - リアクションが欲しい
    - CIにリアクションして怒られるようにする
- 3クリックで電子書籍を書き始める
- 技術文書のサンプルコードのテスト
- textlintについて
- プロジェクトごとに表記揺れのルールを設ける必要性
- 文章に対するCI
- 決してバグ(typo)は無くならない

-----

# 今日扱う「技術文書」の対象

- 技術文書
    - [x] 技術書
    - [x] ブログ
    - [x] スライド
    - [ ] マニュアル
    - [ ] 論文
    
---- 

# 技術書

どのようなツールを使って技術書を開発できるか

## [JavaScript Plugin Architecture](https://github.com/azu/JavaScript-Plugin-Architecture "JavaScript Plugin Architecture")

----

## [JavaScript Plugin Architecture](https://github.com/azu/JavaScript-Plugin-Architecture "JavaScript Plugin Architecture")

- JavaScriptプラグインアーキテクチャについての技術書
- 1章1ライブラリというシンプルな構成
    - jQuery、ESLint、Connect、gulpなどそれぞれが1つの章
- 更新が継続しやすい形を目指した

----

## 技術書に必要な要素(Q)

- MarkdownからHTML/PDF/Epubへの変換
- ファイルのincludeするMarkdown拡張
- サンプルコードのチェック
- Markdown/文章のチェック
- 使いやすいエディタ

----

## 技術書に必要な要素(A)

- **[GitBook](https://www.gitbook.com/)** - MarkdownからHTML/PDF/Epubへの変換
- **[GitBook](https://www.gitbook.com/)** - ファイルのincludeするMarkdown拡張
- **[ESLint](http://eslint.org/)** - サンプルコードのチェック
- **[textlint](https://github.com/azu/textlint "textlint")** - Markdown/文章のチェック
- **好きなMarkdownエディタ** - 使いやすいエディタ

----

# [GitBook](https://www.gitbook.com/)

![fit, gitbook](../img/gitbook.jpg)

----

## What is [GitBook](https://www.gitbook.com/)

- Markdown/AsciiDocで電子書籍を書けるツール/プラットフォーム
- [GitbookIO/gitbook](https://github.com/GitbookIO/gitbook "GitbookIO/gitbook")
    - MarkdownからHTML/PDF/Epub/mobiへの変換
    - 各章を書いて`SUMMARY.md`にリンクを書くだけできる
    - プラグインで拡張が可能
- GitHub Pagesでも公開は簡単

-----

## [gitbook.com](https://www.gitbook.com)

- GitBookの公開プラットフォーム
- HTML/PDF/Epubの自動生成、コミット毎プレビュー、販売/寄付、Organization、アップデート通知、オンラインエディタ
- GitHubとDeployment APIでhookして自動的に反映できる
    - Pull Requestのコミット毎にプレビューできる
    
-----

## GitBookの構造

![fit, right](../img/summary.png)

```
├── README.md
├── Chapters(各章)
│   ├── jquery.md
│   └── ESLint.md
├── SUMMARY.md
└── book.json
```

- `SUMMARY.md` は目次ファイル
- `book.json` はGitBookのメタファイル

-----

## SUMMARY.md

- `SUMMARY.md`には各章へのリンクを貼る
- `SUMMARY.md`は目次ファイル

```
- [jQuery](chapters/jquery.md)
- [ESLint](chapters/ESLint.md)
...
```

----

## GitBookの表示確認

最低限`SUMMARY.md`があればビルドできる

```
npm install -g gitbook-cli
gitbook serve
# open http://localhost:4000
gitbook build
# _books/にHTMLが吐き出される
gitbook pdf|epub|mobi
# pdf epub mobiの出力
```

---

## gitbook.comとの連携

![gitbook integration](../img/gitbook-integration.jpg)

----

## gitbook.comとの連携機能

![right](../img/gitbook-pullrequst.jpg)

- コミット毎にプレビューできる！
    - Pull Requestに対してもプレビューが生成される
    - 自動でHTML/PDF/epub/mobiが生成される
- gitbook.com上で書籍を公開できる

----

## GitBookまとめ

- Markdown/AsciiDocで文章を書ける
- `SUMMARY.md`に目次を書く
- `gitbook build`で電子書籍が出来上がる
- 必要なものがnpm一発で手に入る
- シンプルな構造なので拡張しやすい

----

# 3クリックで電子書籍を書き始める

- 電子書籍を書き始めるのが大変そうに見える
- Node.jsでアプリを書き始めるのと同じぐらい簡単に始めたい
- そんな感じのものを作った

-----

## GitBook Starter Kit

```sh
git clone https://github.com/azu/gitbook-starter-kit.git your-book-name
cd your-book-name
npm install
```

するだけで今日話した内容で技術文書を書き始めることができます！


-----

## Usage: GitBook Starter Kit

```
npm start
```

でプレビュー

```
npm test
```

でテスト

-----

