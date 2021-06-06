# GoogleBooksAPI

google books API
今回は本を検索するAPIを使用しましょう！
ドキュメント：https://developers.google.com/books/docs/overview
できること
google booksに登録されている本のjsonデータを取得できる！
タイトルや著者などで条件を指定できる！
（仕様をよく読みましょう！）
API keyが不要！！！

APIキー
APIにリクエストを送るためにはユニークな文字列が必要．
設定を行ったアプリケーションのみ動作させるため．
（無断で使用されないように．．！）
この文字列をAPIキーを呼び，APIの種類問わず必須の場合が多い．

準備
下記のURLにリクエストしよう！
https://www.googleapis.com/books/v1/volumes
パラメータの追加
今回はタイトルに「firebase」が入っている本を指定して検索してみよう！
上記URLの最後に「?q=intitle:javascript」を追加しよう！
リクエストにはaxiosライブラリを使う！！
JavaScriptでhttp通信を行うためのライブラリ（読み込みが必要）
最近のモダンなフレームワーク（react, vue.jsなど）でも利用されている

```
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>

```

```js
// APIにリクエストを送るときはaxios.get()を使用
axios.get(url)
  .then(function (response) {
    // リクエスト成功時の処理（responseに結果が入っている）
    console.log(response);
  }).catch(function (error) {
    // リクエスト失敗時の処理（errorにエラー内容が入っている）
    console.log(error);
  }).finally(function () {
    // 成功失敗に関わらず必ず実行
    console.log('done!');
  });
```

実行結果

コンソールには以下のようなデータが表示される．

```js
{data: {…}, status: 200, statusText: "", headers: {…}, config: {…}, …}
  config: {url: "https://www.googleapis.com/books/v1/volumes?q=intitle:javascript", method: "get", headers: {…}, transformRequest: Array(1), transformResponse: Array(1), …}
  data:
    items: Array(10)
      0: {kind: "books#volume", id: "yg0fBAAAQBAJ", etag: "lfbwNFyvkDg", selfLink: "https://www.googleapis.com/books/v1/volumes/yg0fBAAAQBAJ", volumeInfo: {…}, …}
      1: {kind: "books#volume", id: "sREfBAAAQBAJ", etag: "Bbo+KCTb+os", selfLink: "https://www.googleapis.com/books/v1/volumes/sREfBAAAQBAJ", volumeInfo: {…}, …}
      2: {kind: "books#volume", id: "EgEfBAAAQBAJ", etag: "1Sqd8Kh1nDE", selfLink: "https://www.googleapis.com/books/v1/volumes/EgEfBAAAQBAJ", volumeInfo: {…}, …}
      3: {kind: "books#volume", id: "oeFeDwAAQBAJ", etag: "VpC+UDGt4ak", selfLink: "https://www.googleapis.com/books/v1/volumes/oeFeDwAAQBAJ", volumeInfo: {…}, …}
      4: {kind: "books#volume", id: "EQ0fBAAAQBAJ", etag: "IUx31Y7bo5w", selfLink: "https://www.googleapis.com/books/v1/volumes/EQ0fBAAAQBAJ", volumeInfo: {…}, …}
      5: {kind: "books#volume", id: "sLiKBgAAQBAJ", etag: "W8AX5pJDoTw", selfLink: "https://www.googleapis.com/books/v1/volumes/sLiKBgAAQBAJ", volumeInfo: {…}, …}
      6: {kind: "books#volume", id: "MMGlDwAAQBAJ", etag: "uasA3kSjFmg", selfLink: "https://www.googleapis.com/books/v1/volumes/MMGlDwAAQBAJ", volumeInfo: {…}, …}
      7: {kind: "books#volume", id: "OH-ynAEACAAJ", etag: "BGSumK/B93U", selfLink: "https://www.googleapis.com/books/v1/volumes/OH-ynAEACAAJ", volumeInfo: {…}, …}
      8: {kind: "books#volume", id: "0pfxN9xhwMIC", etag: "0m0saY33NmY", selfLink: "https://www.googleapis.com/books/v1/volumes/0pfxN9xhwMIC", volumeInfo: {…}, …}
      9: {kind: "books#volume", id: "VI-EoAEACAAJ", etag: "SvupF5US57Q", selfLink: "https://www.googleapis.com/books/v1/volumes/VI-EoAEACAAJ", volumeInfo: {…}, …}
      length: 10
    kind: "books#volumes"
    totalItems: 200
  headers: {cache-control: "private", content-encoding: "gzip", content-length: "7804", content-type: "application/json; charset=UTF-8", date: "Sun, 06 Jun 2021 07:45:18 GMT", …}
  request: XMLHttpRequest {readyState: 4, timeout: 0, withCredentials: false, upload: XMLHttpRequestUpload, onreadystatechange: ƒ, …}
  status: 200
  statusText: ""

```


練習

google books APIを使って下記を実行しよう！
パラメータを自由に設定してURLを作成しよう！
ボタン押下時に，本の情報をconsole.log()で出力しよう！
できる人はブラウザ上に表示もしてみよう！
（タイトルを表示してリンクを張ってみよう！）
