# nuxt-ssr-testing

## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).


## Replication Flow

```sh
yarn create nuxt-app nuxt-ssr-testing
cd nuxt-ssr-testing
mkdir server-middleware
cat << EOF > server-middleware/logger.js
export default function (req, res, next) {
  // req は Node.js の HTTP リクエストオブジェクトです
  console.log(req.url)

  // res は Node.js の HTTP レスポンスオブジェクトです

  // next は 次のミドルウェアを呼び出すための関数です。
  // ミドルウェアがエンドポイントでない場合、関数の最後で next を呼び出すのを忘れないでください！
  next()
}
EOF
yarn add express
cat << EOF > server-middleware/rest.js
const app = require('express')()

app.all('/headers', (req, res) => {
  res.json(req.headers)
})

module.exports = app
EOF
```
