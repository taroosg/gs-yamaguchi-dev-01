# GoogleBooksAPI

## Google Books APIとは

[ドキュメント](https://developers.google.com/books/docs/overview)

本APIに限らず，APIには必ずドキュメント（仕様書）が存在する．

ドキュメントには下記のような重要な情報が記載されているため，必ず目を通そう．

- APIにできること（得られるデータややってくれる処理など）．
- APIの使い方やサンプルコード．
- 料金（無料のものと有料のものが存在する）．

## 特徴

- Google Booksに登録されている本のjsonデータを取得できる！
- タイトルや著者などで条件を指定できる！
- （仕様をよく読みましょう！）
- API keyが不要！！！

>API keyとは
>- APIにリクエストを送るためにはユニークな文字列が必要．
>- 設定を行ったアプリケーションのみ動作させるため．（無断で使用されないように．．！）
>- この文字列をAPIキーを呼び，APIの種類問わず必須の場合が多い．


## 処理の流れ

- APIに定められたURLにリクエストを送信する．
- 送信の際には欲しいデータに必要な条件などを指定する．


## HTTP通信の準備

APIへのリクエストには「HTTP通信」という方式で送信する．

JavaScriptでHTTP通信を行うには下記のような複数の方法が存在する．下のものほどオススメ．

|方法|特徴|
|-|-|
|XMLHttpRequest|生JS / 一番昔から存在する|
|$.ajax()|jQuery / これが出てきて流行った|
|fetch|生JS / 慣れないと分かりづらい|
|axios|ReactとかVueでも使われていて使い勝手が良い|

今回は`axios`ライブラリを使用する．ライブラリであるため，下記のコードで読み込みが必要となる．

最近のモダンなフレームワーク（React, Vue.jsなど）でも利用されているため，今の時点から慣れておくのも良き．

```html
<!-- booksapi.html -->

<script src="https://unpkg.com/axios/dist/axios.min.js"></script>

```


## リクエストの送信とデータの受け取り

Google Books APIで指定された下記のURLにリクエストする．

`https://www.googleapis.com/books/v1/volumes`

リクエストの際には，得たいデータの条件などを指定する．

- 今回は「本のタイトルに`javascript`が含まれる」という条件を指定してみる．
- 本条件を指定する場合は，上記URLの最後に「`?q=intitle:javascript`」を追加する．
- 条件の指定の仕方はドキュメントに記載されている．APIによって指定方法が異なるため，必ずドキュメントを確認しよう．

リクエストは`axios.get()`関数で実行する．

```js
// booksapi.html

const requestUrl = 'https://www.googleapis.com/books/v1/volumes?q=intitle:javascript';

axios.get(requestUrl)
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

### リクエストを送信する`axios.get()`の動き方

`axios.get()`関数の`.then()`などは実行されるタイミングが下記のように決まっている．

|記述|実行されるタイミング|
|-|-|
|`.then(function (response) {...})`|情報の取得に成功した場合に`{}`内が実行される．<br>取得した情報は`response`に格納されている．|
|`.catch(function (error) {...}`|情報の取得に失敗した場合に`{}`内が実行される．<br>エラーの詳細が`error`に格納されている．|
|`.finally(function () {...}`|情報の取得成否にかかわらず`{}`内が実行される．|

### 処理の順番

したがって，リクエストの成否によって下記のどちらかの順番で処理が実行されることとなる．

- リクエスト成功の場合
    1. `.then(function (response) {...})`の`{}`内に記述した処理．
    2. `.finally(function () {...}`の`{}`内に記述した処理．
- リクエスト失敗の場合
    1. `.catch(function (error) {...})`の`{}`内に記述した処理．
    2. `.finally(function () {...}`の`{}`内に記述した処理．

### 💡 Key Point

>重要なのはリクエストに成功した場合の処理である．
>
>APIから取得したデータを使いたい場合は`.then(function (response) {...})`の`{}`内に処理を記述しよう．


## 実行結果

上記のコードを実行すると，コンソールには以下のようなデータが表示される．

データ全体はオブジェクトとなっており，`data.items`に本のデータが配列形式でまとまっている．ブラウザの検証画面をみてデータ構造や本のタイトルがどこに含まれているのかなど確認しよう．

```js
// 検証画面に表示される内容

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


## 練習

Google Books APIを使って下記を実行しよう！

1. 検索の条件を自由に設定してURLを作成しよう！
2. 本の情報をconsole.log()で出力しよう！
3. 本のタイトルをブラウザ上に一覧表示してみよう！
4. （タイトルにリンクを張る，本の画像を表示，などもチャレンジ）
