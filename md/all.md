# 技術文書をソフトウェア開発する話

技術文書の自動テスト、開発プロセスについて

----

# 自己紹介

![アイコン](https://github.com/azu.png)

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

# 今日話す「技術文書」の対象

- 技術文書
    - Y ブログ 
    - Y 技術書
    - Y スライド
    - N マニュアル
    - N 論文
    
---- 

# [GitBook](https://www.gitbook.com/)

![fit, gitbook](../img/gitbook.jpg)

----

# [GitBook](https://www.gitbook.com/)

- Markdownで電子書籍を書けるツール/プラットフォーム
- [GitbookIO/gitbook](https://github.com/GitbookIO/gitbook "GitbookIO/gitbook")
    - MarkdownからHTML/PDF/Epubへの変換
    - 各章を書いて`SUMMARY.md`にリンクを書くだけできる
    - プラグインで拡張が可能
- GitHub Pagesでも公開は簡単

-----

# [gitbook.com](https://www.gitbook.com)

- GitBookの公開プラットフォーム
- HTML/PDF/Epubの自動生成、コミット毎プレビュー、販売/寄付、Organization、アップデート通知、オンラインエディタ
- GitHubとDeployment APIでhookして自動的に反映できる

-----

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

