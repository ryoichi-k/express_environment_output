# expressでのnode.js、Reactアプリ環境構築手順のアウトプット

環境：MacOS

npm: 8.5.1

node: v17.6.0

React 18.2.0

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
dotenv→node.jsで環境変数使用できる。これで.envファイルが使える。
```
npm i express mongoose nodemon helmet dotenv
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
    "dotenv": "^16.0.1",
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
セキュリティ上.envも忘れないように。
```
node_modules
package-lock.json
.env
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

## ステップ8 内部情報をenvファイルに追記
DB接続情報はenvファイルに記述し、githubに上がらない様にする。
dotenvをインストールしていればすぐに使用できる。
```.env
#DB_MySQL
HOST=localhost
PORT=8000
USER=root
PASSWORD=passpasspassdayo
DATABASE_NAME=naninanidb
```
上記を呼び出すには、
```index.js
//requireの下に追記
require("dotenv").config();
//以下の形式で呼び出し
process.env.PORT;
process.env.USER;
```

## ステップ9 フロント側react
以下コマンドで新規reactプロジェクト作成（3分くらいかかる）。Happy hacking!　と出たら成功。
```
npx create-react-app sns-front
```
サーバー立ち上がるか確かめる（自動でlocalhost:3000が立ち上がる。）Reactのロゴが回転していたら正常。
```
cd sns-front
npm start
```

## ステップ10 余計なファイル削除
public内のlogoファイル２つ、test系のファイルも削除。
src内はApp.jsとindex.jsを残してあとは削除で良い。
下記のような状態にする。

App.js
```App.js
function App() {
  return (
    <div className="App">

    </div>
  );
}

export default App;

```
index.js
```index.js
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

## ステップ11 githubにpush
デフォでgit initはされていて、gitignoreもあるので、コミットしたらgithubと連携してしまって良い。
