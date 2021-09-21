# 課題と提出時の注意点

**Firebaseを使用したアプリを実装しよう！**

Firebaseを用いることで複数の端末での双方向的なやり取りを実装することが可能となる．

今回はデータを追加していく方式で実装したが，データを削除したり上書きしたりすることも可能だ．

今回使用したFirestore以外にも様々な機能がある．本気出せばWebアプリケーションを全て実装してデプロイできるだけの可能性を秘めた技術であるッ！

- 認証（Authentication）
- ファイル保存（Storage）
- デプロイ（Hosting）
- サーバサイドの実装（Functions）

## 実装例

- スタンプ送信機能
- オンラインでじゃんけん
- 出席管理システム
- オリジナルSNS
- MMORPGを開発

## ⚠️ 注意点

### APIキーの扱い

- FirebaseにはAPIキーが必要になります．
- 誰でも見られるGithubにあげてしまうとあまりよろしくない．

Githubにpushする前に．．．

- `git add .`する前にAPIキー部分は一旦削除しておきましょう．
- 提出フォームのコメント欄にAPIキーを記述してください！

```html
<script type="module">
  import { initializeApp } from "https://www.gstatic.com/firebasejs/9.0.2/firebase-app.js";
  import { getFirestore, collection, addDoc, serverTimestamp, query, orderBy, onSnapshot, } from "https://www.gstatic.com/firebasejs/9.0.2/firebase-firestore.js";

  const firebaseConfig = {
    // 🔽この1行を`git add .`する前に一旦削除！削除したAPIキーは「提出フォームのAPIkey欄」に記述！
    apiKey: "AIzaSyD7uBPYxKsUJQrJ94D8Ss5Ss5ETRpUzNbs",
    authDomain: "chatapp-4cdef.firebaseapp.com",
    projectId: "chatapp-4cdef",
    storageBucket: "chatapp-4cdef.appspot.com",
    messagingSenderId: "647489237948",
    appId: "1:647489237948:web:1a75f2713344937854f1b9"
  };

  const app = initializeApp(firebaseConfig);

  // 以下，JavaScriptのコードたくさん

</script>

```

