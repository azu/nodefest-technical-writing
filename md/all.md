# 技術文章をソフトウェア開発する話

技術文章の自動テスト、開発プロセスについて

----

# アジェンダ


- 3クリックで電子書籍を書き始める
- 技術文章のサンプルコードのテスト
- textlintについて
- プロジェクトごとに表記揺れのルールを設ける必要性
- 文章に対するCI
- 決してバグ(typo)は無くならない

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

するだけで今日話した内容で技術文章を書き始めることができます！


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