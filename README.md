# express_environment_output

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
⇨アプリのファイルにpackage.jsonが作成されていることを確認


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
