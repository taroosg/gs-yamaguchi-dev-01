# Firebase の準備 2（ソースコードの準備）

## プロジェクトと JavaScript の連携

画面の下記部分をクリックする．

![Webアプリ追加](./img/20210616122043.png)

ニックネームを入力するよう促されるので適当に入力する（プロジェクト名と同じが良い？）．

「Firebase Hosting」の ✅ は入れないこと．「アプリを登録」をクリックすると次の画面に切り替わる．

![ニックネーム設定](./img/20210616122207.png)

コードが表示されるので全てコピーする．

![コードコピー](./img/20210921105725.png)

`chatapp.html`にコピーしたコードを貼り付ける．このコードが Firebase のプロジェクトとソースコードでやり取りをするために必要になる．

エディタ上で下記のような状態になっていれば OK（コメントは省略）！

```html
<!-- chatapp.html -->

<!-- ここにFirebaseのコードを貼り付けよう -->
<script type="module">
  import { initializeApp } from "https://www.gstatic.com/firebasejs/9.0.2/firebase-app.js";

  const firebaseConfig = {
    apiKey: "AIzaSyAfiXSG63mRJrfnWb2pSHH-tCUtPptP-Qw",
    authDomain: "test-466a4.firebaseapp.com",
    projectId: "test-466a4",
    storageBucket: "test-466a4.appspot.com",
    messagingSenderId: "1012034593201",
    appId: "1:1012034593201:web:9d9dbbd31cf63275761d90",
  };

  const app = initializeApp(firebaseConfig);
</script>
```

コードを貼り付けたらブラウザ画面の「コンソールに進む」ボタンをクリックする．
