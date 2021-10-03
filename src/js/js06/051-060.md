## プロフィールの表示

人事局長のあなたは，毎年行われる新入社員の自己紹介が面倒なので自動化するシステムをつくることにしました．

名前`name`，年齢`age`，性別`gender`が記載されたオブジェクトを入力すると，プロフィールを出力する`outputProfile()`関数を作成してください．

プロフィールの形式は「彼/彼女の名前は`name`で`age`歳です」とします．彼/彼女はgenderによって区別されるものとします．

3項目揃っていない場合は「情報がありません」と出力してください．

```js
function outputProfile(obj) {

}
const taro ={
  name : 'Taro',
  age : 25,
  gender : 'male',
};

console.log(outputProfile(taro));    //彼の名前はTaroで25歳です

const hanako = {
  name : 'Hanako',
  age : 30,
  gender : 'female',
};

console.log(outputProfile(hanako));    // 彼女の名前はHanakoで30歳です

const hatena = {
  name: 'hatena',
  age: 20,
};

console.log(outputProfile(hatena));   //  情報がありません
```


## お買い物リスト

配列でつくられた買い物リストがあります．

買い物に出かけようとしたタイミングで新たにリストに追加しましたが，バグで別の配列に入ってしまいました．

二つの配列を合わせた新しい配列を出力する`combineArray()`関数を作成してください．

```js
function combineArray(a, b) {

}

const abc = ["a", "b", "c"];
const def = ["d", "e", "f"];

console.log(combineArray(abc, def));    //["a", "b", "c", "d", "e", "f"]

const gen = ["米", "トイレットペーパー", "ちゅーる", "酒"];
const yui = ["洗剤", "肉", "ブロッコリー"];

console.log(combineArray(gen, yui));    // ["米", "トイレットペーパー", "ちゅーる", "酒", "洗剤", "肉", "ブロッコリー"]
```


## 成績を晒す

あなたが勤務する学校で小テストを行いました．成績の悪い生徒を晒したく，テストのスコアが悪い順に出力するプログラムを作成しましょう．

テストの点数は半角スペース区切りで入力されるため，点数が低い順に半角スペース区切りで出力する`createBadScoreArray()`関数を作成してください．

```js
function createBadScoreArray(a) {

}

console.log(createBadScoreArray('15 8 9 100 26 1'));    // 1 8 9 15 26 100

console.log(createBadScoreArray('50 15 89 5 61 2 44'));    // 2 5 15 44 50 61 89
```


## 特定の文字列を含むか

文字列の中に，特定の文字列が含まれているかの判定を出力する`containStrings()`関数を作成してください．

含まれている場合は「`true`」含まれていない場合は「`false`」と出力することとします．

```js
function containStrings(str1, str2) {

}

const a = "あけましておめでとうございます";
const b = "おめでとう";

console.log(containStrings(a, b));    // true

const c = "Love the life you live. Live the life you love.";
const d = "best";

console.log(containStrings(c, d));    // false
```


## アンケートデータの作成

名前と年齢を入力するアンケートを作成しました．回答データを扱いやすくするため，一つのオブジェクトにまとめたデータを作成したいと考えました．

入力データ（名前と年齢）からこれら2つ（`name`, `age`）をキーとしたオブジェクトを出力する`createObject()`関数を作成してください．

```js
function createObject(a, b) {

}

console.log(createObject('ichiro', 20));    // { name: "ichiro", age: 20, }
console.log(createObject('momoko', 22));    // { name: "momoko", age: 22, }
```


## ランダムに挨拶

プロジェクトのチャットツールで挨拶をすることになりました．

いろいろな国や地域から参加者がいるため，時差などを考慮した挨拶を考えるのが面倒なのでランダムに出力してお茶を濁すことにしました．

予め決めた挨拶を入力すると，ランダムに一つの挨拶を出力する`randomGreet()`関数を作成してください．

```js
function randomGreet(a, b, c) {

}
console.log(randomGreet('おはよう','こんにちは','こんばんは'));   // おはようorこんにちはorこんばんは
console.log(randomGreet('Hi!','Hello!','Bye!'));   // Hi! or Hello! or Bye!
```


## オブジェクトの並び替え

膨大な顧客データの中から，条件に当てはまる顧客のリストをつくっています．

リストは並び順が適当なので，管理番号が若い順に並び替えたリストに直しましょう．

管理番号`id`，名前`name`，年齢`age`を定義するオブジェクトobjを入力すると，`id`の順番で並び替えたメンバーの一覧を出力する`sortObject()`関数を作成してください．一人のデータは`id:name(age)`形式となるようにし，`,`で区切った文字列にすること．

```js
function sortObject(obj) {

}

const objectArray1 = [
  {
    id: 8,
    name: "Emily",
    age: 29,
  },
  {
    id: 1,
    name: "John",
    age: 22,
  },
  {
    id: 4,
    name: "Bob",
    age: 30,
  },
];

console.log(sortObject(objectArray1));   // 1:John(22),4:Bob(30),8:Emily(29)

const objectArray2 = [
  {
    id: 10,
    name: "taro",
    age: 29,
  },
  {
    id: 112,
    name: "hanako",
    age: 22,
  },
  {
    id: 40,
    name: "pochi",
    age: 3,
  },
];

console.log(sortObject(objectArray2));    // 10:taro(29),40:pochi(3),112:hanako(22)
```


## 名前しかいらん

顧客リストを作成する仕事を任されました．完成させて上司に提出したところ，「名前しかいらん」と言われました．

これまでに作成した顧客リストを活用したいので，これらのデータから名前だけを抽出しましょう．

管理番号`id`，名前`name`，年齢`age`，を定義するオブジェクトを入力して，名前のみの配列を出力する`createNameArray()`関数を作成してください．

```js
function createNameArray(array) {

}

const objectArray3 = [
  {
    id: 8,
    name: "Emily",
    age: 29,
  },
  {
    id: 1,
    name: "John",
    age: 22,
  },
  {
    id: 4,
    name: "Bob",
    age: 30,
  },
];

console.log(createNameArray(objectArray3));   // ["John", "Emily", "Bob"]

const objectArray4 = [
  {
    id: 10,
    name: "taro",
    age: 29,
  },
  {
    id: 112,
    name: "hanako",
    age: 22,
  },
  {
    id: 40,
    name: "pochi",
    age: 3,
  },
];
console.log(createNameArray(objectArray4));   // ["pochi", "hanako", "taro"]
```


## メール一斉送信

顧客リストの中から，25歳以下のメンバーにメールの一斉送信を行う仕事を任されました．

管理番号`id`，名前`name`，年齢`age`を定義するオブジェクトを引数として，25歳未満のメンバーの`id`が入った配列を出力する`filterUnder25Array()`関数を作成してください．

```js
function filterUnder25Array(array) {

}

const objectArray5 = [
  {
    id: 8,
    name: "Emily",
    age: 29,
  },
  {
    id: 1,
    name: "John",
    age: 22,
  },
  {
    id: 4,
    name: "Bob",
    age: 30,
  },
];

console.log(filterUnder25Array(objectArray5));   // [1]

const objectArray6 = [
  {
    id: 10,
    name: "taro",
    age: 29,
  },
  {
    id: 112,
    name: "hanako",
    age: 22,
  },
  {
    id: 40,
    name: "pochi",
    age: 3,
  },
];

console.log(filterUnder25Array(objectArray6));   // [112, 40]
```


## 予算オーバー

ECサイトで買い物をした商品がカートに入っています．このサイトはバグを抱えており，合計金額がユーザに表示されません．

カートの中身から合計金額を算出し，今回の予算`¥114514`に収まるかどうかを判断しましょう．

カート内の情報を入力すると商品の価格`price`合計が予算に収まるかどうかを`true`または`false`で出力する`canTakeThis()`関数を作成してください．

カートには商品が複数入る場合（`count`の値）がある点に注意しましょう．

```js
function canTakeThis(arr) {

}
const tarosCart = [
  {
    id: 8,
    name: "Yoich",
    price: 5800,
    count: 2,
  },
  {
    id: 1,
    name: "Yamasaki30",
    price: 3000000,
    count: 1,
  },
  {
    id: 4,
    name: "Chita",
    price: 3600,
    count: 1,
  },
];

console.log(canTakeThis(tarosCart));    // false

const hanakosCart = [
  {
    id: 10,
    name: "ひまわり",
    price: 280,
    count: 3,
  },
  {
    id: 112,
    name: "かすみ草",
    price: 220,
    count: 2,
  },
  {
    id: 40,
    name: "ガーベラ",
    price: 110,
    count: 5,
  },
];
console.log(canTakeThis(hanakosCart));    // true
```
