# expressでのnode.jsアプリ環境構築手順のアウトプット

環境：MacOS

npm: 8.5.1

node: v17.6.0

## ステップ１　アプリの開発フォルダを作成アンド移動
```
$ mkdir app_name
$ cd app_name
```

## ステップ2　node.jsとnpmのバージョン確認
```
node -v
npm -v
```

## ステップ3　 npm initでnode.jsの新規アプリ作成
```
npm init
```
その後の質問には、エントリーポイントにはserver.jsという名前にする。authorに自分の名前を入れておく

## ステップ4　 各種ライブラリインストール
express→フレームワーク
mongoose→mongoDBとの連携に必要
helmet→アプリのセキュリティ強化のためにインストール
nodemon→サーバーをバックで起動できる。デーモン
```
npm i express mongoose nodemon helmet
```



こんなのが出たら完了
```
added 119 packages, and audited 120 packages in 11s

14 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```
⇨アプリのフォルダ内にpackage.jsonが作成されていることを確認


```package.json
"dependencies": {
    "express": "^4.18.1",
    "helmet": "^5.1.1",
    "mongoose": "^6.5.2",
    "nodemon": "^2.0.19"
  }
```

## ステップ5 gitリポジトリ化する
vscode上でgitの認証が発生する場合あり。その場合は認証する。
```
git init
git add .
```

## ステップ6 .gitignore作成
gitignoreに以下を記述する。特にnode_modulesを忘れないこと（vscode上でステージングから下ろせるのでリカバリーは効くので大丈夫です。）
```
node_modules
package-lock.json
```

## ステップ7 server.jsの設定（このファイルがサーバーになるイメージ）
localhost:3000でブラウザでaiueoが表示されるかを確認
```server.js
const express = require('express');
const app = express();

const port = 3000;


app.get("/", (req, res) => {
    res.send("aiueo")
})

// ポート番号を付与したアクセスURLを実行
app.listen(port, () => {
    console.log(`App listening at http://localhost:${port}`);
})

```
