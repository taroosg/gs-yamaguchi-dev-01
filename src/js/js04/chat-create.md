# チャット画面の実装とデータの送信

## チャット画面の実装

nameとtextの入力欄を作成する．

送信時にidを指定して入力した値を取得するため，`<input>`タグの2箇所と`<button>`にidを指定する．

```html
<!-- chatapp.html -->

<form>
  <fieldset>
    <legend>チャット入力画面</legend>
    <div>
      name: <input type="text" id="name">
    </div>
    <div>
      text: <input type="text" id="text">
    </div>
    <div>
      <button type="button" id="send">send</button>
    </div>
  </fieldset>
</form>

```

下図のような画面となる．

![チャット入力画面](./img/20210616144514.png)


## データ送信の処理

続いて，上記の入力画面でnameとtextを入力して送信ボタンをクリックしたタイミングでFirestore上に新しいデータを作成する処理を実装する．

### リアルタイム通信の準備

前項で作成したコレクションとやり取りをするため，下記のコードを追記する．追記場所は張り付けたFirebase関連のコード下くらいでOK．

### 💡 Key Point

>このコードでは`chat`コレクションの接続情報を`db`に保存する．この1行を書いておくことで`db`に対してデータの追加や取得ができるようになる．

```js
// chatapp.html

const db = firebase.firestore().collection('chat');

```

### 送信ボタンクリック時にデータを送信

続いて，送信ボタンクリック時にデータを送信する処理を実装する．

まずはボタンのクリックイベントを作成．

```js
// chatapp.html

$('#send').on('click', function () {
  // 送信時に必要な処理
});

```

続いてクリックイベント内に「入力値を取得する処理」と「データを送信する処理」を記述する．

ポイントは，

- id指定して`.val()`で入力値を取得する．
- データを送信する際にはオブジェクト形式にする必要がある．
- `time`はFirestoreの独自形式となるため，Firestore側で用意されている関数を使用する．

```js
// chatapp.html

const data = {
  name: $('#name').val(),
  text: $('#text').val(),
  time: firebase.firestore.FieldValue.serverTimestamp(),
};
db.add(data);
$('#text').val('');

```


## 動作確認

コードを記述したらブラウザの画面から`name`と`text`を入力して．．．

![動作確認（ブラウザ）](./img/20210616145454.png)

Firebaseのコンソール画面でデータが保存されていればOK！

![動作確認（コンソール）](./img/20210616145647.png)

## 練習

下記の処理を実装し，Firestoreにデータを保存しよう！

1. 入力画面の作成
2. データの送信処理
