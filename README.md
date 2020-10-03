# nuxt-skill-map
Nuxt.jsで作るスキルマップ

## 開発手順

```bash
$ npm install

$ npm run dev
```

## ビルド
```bash
$ npm run build
$ npm run start
$ npm run generate
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
nuxt.config.jsの中でかける  
以下追加。

```js
  generate: {
    dir: 'docs',
  },
```
