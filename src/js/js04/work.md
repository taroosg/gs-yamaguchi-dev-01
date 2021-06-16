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
<script>
  // Your web app's Firebase configuration
  var firebaseConfig = {
    // 🔽この1行を`git add .`する前に一旦削除！削除したAPIキーは「提出フォームのAPIkey欄」に記述！
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

