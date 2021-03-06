# nuxt-skill-map
Nuxt.jsで作るスキルマップ

## DEMO
https://yuki-sakaguchi.github.io/nuxt-skill-map/

## 開発手順

```bash
$ npm install

$ npm run dev
```

## ビルド
GitHub Pages用に設定をカスタマイズしているのでそっちを使う
```bash
$ npm run generate:gh-pages
```

# メモ

## 準備
```bash
npx create-nuxt-app nuxt-skill-map
```

## ドラッグ&ドロップ用のライブラリを読み込む
[vue-drag-resize](https://www.npmjs.com/package/vue-drag-resize)

```bash
npm i vue-drag-resize
```

## ダークモードが嫌なので止める
`nuxt.config.js`の`dark`をfalseにする。

## GitHub Pagesで公開するためにgenerate先を`docs`に
nuxt.config.jsの中に以下追加。  

```js
  generate: {
    dir: 'docs',
  },
```

その他も設定が必要だけど公式で解説してくれてるのでこれ通りやる。  
https://ja.nuxtjs.org/faq/github-pages/

