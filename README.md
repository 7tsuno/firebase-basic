# FirebaseでBasic認証付きのページを上げる

## 前提

* `Node.js`,`npm`が入っていること
* googleアカウントがあること

## How to use this

### 1. ブラウザでプロジェクトを作る。

https://console.firebase.google.com/

プロジェクト名はなんでもいい  
プロジェクトIDをメモっておく

### 2. このプロジェクトをクローン

```bash
git clone https://github.com/7tsuno/firebase-basic
cd firebase-basic
```

### 3. firebase cliをインストール

```bash
npm install -g firebase-tools
```

ログインしておく

```bash
firebase login
```

OAuthが出るので適切なアカウントでログイン。

### 4. npmライブラリインストール

```bash
cd functions
npm i
cd ../
```

### 5. 設定ファイルを書き換える

`.firebaserc`を書き換える


```
{
  "projects": {
    "default": "ここにプロジェクトIDを記載する"
  }
}
```

### 5. deploy

```bash
firebase deploy
```

Deploy complete!

と出れば成功。URLにアクセスするとBasic認証が出来る。  

## ID/PASS

初期は user : user / password : pass でログインできる。  
変更する場合は`functions/index.js`をいじる

```js
app.all('/*', basicAuth(function(user, password) {
  return user === 'user' && password === 'pass';
}));
```

## 資材

`functions/static`ディレクトリ配下に入れる。
