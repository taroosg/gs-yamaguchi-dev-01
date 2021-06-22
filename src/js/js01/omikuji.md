# おみくじのWebアプリ実装

おみくじの処理自体はできたが，画面から操作できるWebアプリケーションにしたい！

## 想定される挙動

- 画面上のHTML要素（DOM）をクリックして処理を実行！
- 要素を「指定」する！
- classやidでDOMを特定する．
- 指定したDOMに対してJavaScriptで操作を行う！

例

- 「idがbutton」の要素を「クリック」したら．．．
- 「大吉-大凶のどれかをランダムに表示」！

参考（DOM）

>HTMLに記述されている各要素のこと（document object model）

基本の3要素

selector
（どこを）

event
（いつ）

method
（どうする）

![dom3要素](./img/20210622123450.png)

なんだけど．．．

JavaScriptはDOM操作が苦手．．．

## jQueryライブラリ

【重要】最初に読み込みが必要！

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
```

cssと同じ要領で対象箇所を指定できる
素のJavaScriptよりも短く書ける！			<- 重要
アニメーションなど手軽に設定できる．
書き方（順序や考え方）はJavaScriptと同様！	<- 重要
導入が簡単（フレームワークなどは環境構築で詰む）
jQueryはJavaScriptを短縮して書けるライブラリ
    【参考】https://webkikaku.co.jp/homepage/blog/hpseisaku/webdesign/jquery_start/


![dom3要素](./img/20210622123450.png)

```js
$('#button').on('click', function () {
  alert('Hello World!');
});

```

```js
$(`セレクタ名`).on(`イベント名`, function () {
  `実行したい処理（メソッド）`
});

```

たくさんあります
「jQuery セレクタ」でググる！
「jQuery イベント」でググる！


## まずは形の入力に慣れよう！

```js
$('#id').on('click', function () {
  // ...
});

```

### 喋りながら書くと定着する（本当）

>  だらーあいでぃーおんくりっくふぁんくしょんかっこかっこなみかっこえんたー...


## 練習

おみくじアプリケーションを完成させよう！

### 仕様

- 「おみくじを引くボタン」をクリックしたら以下のどれかを画面に表示！
- 「大吉・中吉・小吉・凶・大凶」

### ヒント

下記の流れで考えよう！

- ボタンをクリックしたらなにかする．
- ランダムな数値を発生させる．
- 条件分岐をつくって，対応する「大吉，中吉，...」を画面に表示させる．

```js
$('#button').on('click', function () {
  // 0から4でランダムな数を作成
  // 0だったら大吉，1だったら中吉．．．
  // 結果をidで指定した場所に表示
});

```

