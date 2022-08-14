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

## ステップ4　 各種インストール
express→フレームワーク
mongoose→mongoDBとの連携に必要
helmet→アプリのセキュリティ強化のためにインストール
nodemon→サーバーをバックで起動できる。デーモン
```
npm i express mongoose nodemon helmet
```
