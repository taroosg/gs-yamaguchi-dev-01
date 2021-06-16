# Firebaseの準備2（ソースコードの準備）

## プロジェクトとJavaScriptの連携

画面の下記部分をクリックする．

![Webアプリ追加](./img/20210616122043.png)

ニックネームを入力するよう促されるので適当に入力する（プロジェクト名と同じが良い？）．

「Firebase Hosting」の✅は入れないこと．「アプリを登録」をクリックすると次の画面に切り替わる．

![ニックネーム設定](./img/20210616122207.png)

コードが表示されるので全てコピーする．

![コードコピー](./img/20210616122317.png)

`chatapp.html`にコピーしたコードを貼り付ける．このコードがFirebaseのプロジェクトとソースコードでやり取りをするために必要になる．

貼り付けた`<script>`タグの中身を修正する．

>修正前
>
>`<script src="https://www.gstatic.com/firebasejs/8.6.7/firebase-app.js"></script>`

>修正後
>
>`<script src="https://www.gstatic.com/firebasejs/8.6.7/firebase.js"></script>`

エディタ上で下記のような状態になっていればOK！

```html
<!-- chatapp.html -->
<!-- ここにFirebaseのコードを貼り付けよう -->

<!-- The core Firebase JS SDK is always required and must be listed first -->
<script src="https://www.gstatic.com/firebasejs/8.6.7/firebase.js"></script>

<!-- TODO: Add SDKs for Firebase products that you want to use
     https://firebase.google.com/docs/web/setup#available-libraries -->

<script>
  // Your web app's Firebase configuration
  var firebaseConfig = {
    apiKey: "AIzaSyBPm676fTHNHq2_hogehoge_wryyyyyy",
    authDomain: "chat-app-test-4e1e4.firebaseapp.com",
    projectId: "chat-app-test-4e1e4",
    storageBucket: "chat-app-test-4e1e4.appspot.com",
    messagingSenderId: "929064315016",
    appId: "1:929064315016:web:79dd676be9a71b1803173d"
  };
  // Initialize Firebase
  firebase.initializeApp(firebaseConfig);
</script>

```

コードを貼り付けたらブラウザ画面の「コンソールに進む」ボタンをクリックする．