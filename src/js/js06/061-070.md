## トランプ占い

著名な占い師であるあなたはとある国の大統領から占いを依頼されました．正しい占いをしたいところですが，この大統領は気難しいのであまり悪い結果を伝えるのはためらわれます．

占いの結果はトランプカード"J", "Q", "K"の2枚1組で表れます．

もし結果が「最悪」を表す"J"2枚になってしまったときには片方（2枚目） を"Q"に変更する`divinationCheat()`関数を作成してください．

```js
function divinationCheat(s) {

}

console.log(divinationCheat('K Q'));    // K Q
console.log(divinationCheat('J Q'));    // J Q
console.log(divinationCheat('J J'));    // J Q
```


## AボタンとBボタン

あなたはAのボタン， Bのボタンの2つのボタンを使うゲームを作っています．

このゲームではキャラクターを動かして遊びます．キャラクターははじめ座標0の位置にいて，Aのボタンを押すとキャラクターが1マス右に進み（座標が1増える）， Bのボタンを押すとキャラクターが1マス左に進み （座標が1減る） ます．

A, Bのボタンそれぞれ何回押したが入力されるので，ボタンが全て押された後のキャラクターの位置の座標を出力する`placeCount()`関数を作成してください．

```js
function placeCount(s) {

}

console.log(placeCount('3 4'));    // -1
console.log(placeCount('80 44'));    // 36
```


## 3倍返し？

バレンタインデーも終わり，あなたはホワイトデーにいくつチョコレートを用意すればよいかを計算するプログラムを作ることにしました．

もらったチョコレートが1つ以上であればその3倍の数を， 0個であれば自分用に1つだけ用意することにしましょう...

もらった個数`n`が入力されるので，お返しの数を出力する`deathWhiteDay()`関数を作成してください．

```js
function deathWhiteDay(n) {

}

console.log(deathWhiteDay(1));    // 3
console.log(deathWhiteDay(99));    // 297
console.log(deathWhiteDay(0));    // 1
```


## Leet文字列

Leetと呼ばれるインターネットスラングがあります．

Leetではいくつかのアルファベットをよく似た形の他の文字に置き換えて表記します．
Leetの置き換え規則はたくさんありますが，ここでは次の置き換え規則のみを考えましょう．

|置き換え前|置き換え後|
| :---: | :---: |
| A |	4 |
| E |	3 |
| G |	6 |
| I |	1 |
| O	| 0 |
| S |	5 |
| Z |	2 |


文字列が入力されるので，これをLeetに変換して出力する`convertLeet()`関数を作成してください．

```js
function convertLeet(s) {

}

console.log(convertLeet('ALANTURING'));    // 4L4NTUR1N6
console.log(convertLeet('GSACADEMY'));    // 654C4D3MY
```


## 完全数とほぼ完全数

N を 2 以上の整数とし，N の約数のうち N 自身を除いたものの和を S とします． このとき

- N = S となるような N を完全数
- |N-S| = 1 となるような N をほぼ完全数

と言うことにしましょう．ここで，|N-S| は N-S の絶対値を意味します．

たとえば，N = 28 のとき，28の約数は 1, 2, 4, 7, 14, 28 なので，S = 1+2+4+7+14 = 28 となります．従って，28は完全数です．

また，N = 16 のときには S = 1+2+4+8 = 15 となるので，16はほぼ完全数です．

入力された整数が完全数かほぼ完全数かそのいずれでもないかを判定する`isPerfectNumber()`関数を作成してください．

判定は以下のとおりとします．

|完全数|ほぼ完全数|それ以外|
|:---:|:---:|:---:|
|perfect|nearly|neither|

```js
function isPerfectNumber(s) {

}

console.log(isPerfectNumber('28 16 777'));    // perfect nearly neither
console.log(isPerfectNumber('3 4 5 6'));    // neither nearly neither perfect
```


## 単語テストの採点

英単語のテストの採点ではどこまでをスペルミスとみなしてどこまでを別の単語とみなすかが悩みどころです．

そこでジーズ予備校では以下の様な採点基準を導入してこれに従って厳密に採点することにしています．

|||
|----|----|
|正解の単語と完全一致| ◯ 2 点 |
|正解の単語と長さ（文字数）が異なる| × 0 点|
|正解の単語と長さは同じだが1文字だけ異なる| △ 1 点|
|正解の単語と長さは同じだが2文字以上異なる| × 0 点|

ここで「文字が異なる」とは，同じ位置にある文字が異なるということを意味しています．

【例】

|正解|回答|点数|
|---|---|---|
| apple | aple | 0 点 (長さが異なる)|
| orange | olange | 1 点 (長さは同じだが 1 文字だけ異なる)|
| grape | glepe | 0 点 (長さは同じだが 2 文字異なる)|
| lemon | lemon | 2 点 (完全一致)|

合計得点 → 3 点

問題数と各問題の正解の単語および生徒の解答が与えられるので，このような形でジーズ予備校の採点基準に従いこの生徒の合計得点を算出する関数を`calculatePoint()`作成してください．

正解と回答を半角スペースで区切ったものを1セットとし，各セットがカンマ区切りで入力されます．



```js
function calculatePoint() {

}

console.log(calculatePoint('apple aple,orange olange,grape glepe,lemon lemon'));    // 3
console.log(calculatePoint('january januarry,february febrary,march march,april aplil,may may,june june,july jury,august ougust,september septenber,october october,november novembar,december dicembar'));    // 13
```


## 先生の宿題

あなたは小学校一年生の先生です．今週の授業で，足し算と引き算を教えます．

あなたは，足し算と引き算を用いた宿題を作る必要があり，そのためのプログラムを書くことにしました．

以下の手順で問題をランダム生成するプログラムはもうできているのですが，その答えを求めるプログラムはまだできていません．

【問題生成の手順】

1. 正しい式 a + b = c, あるいは a - b = c (a, b, c, は整数) を生成する
2. a, b, c のうちいずれか 1 つを空欄にする

この空欄に入れるべき整数が「答え」となります．

式を入力したら式中のxで表した答えを出力する`getAnswer()`関数を作成してください．

```js
function getAnswer() {

}

console.log(getAnswer('1 + 3 = x'));    // 4
console.log(getAnswer('6 - x = 3'));    // 3
console.log(getAnswer('x - 1 = 5'));    // 6
```


## アニメの日時

深夜アニメの放送開始時刻は，しばしば "時" を表す部分の数字が24以上になることを許容し次のように表記することがあります．

`01/27 24:30`

この日付を "時" の部分が0以上23以下になるような表記で，

`01/28 00:30`

と表すことができます．

前者の表記方法は時として便利ではありますが，実際に放送される "日" が知りたい場合は後者のほうが便利です．


そこで，日時が与えられるので，"時" の部分が 0 以上 23 以下になるように修正した日時を出力する`formatHour()`関数を作成してください．

ただし，"時" を修正した結果，日がその月に存在しない日になった場合でも月を調整することなくそのまま出力してください．もしかすると，この関数が使われる世界ではそのような日付が存在するかもしれないからです．

```js
function formatHour() {

}

console.log(formatHour('01/27 24:30'));    // 01/28 00:30
console.log(formatHour('02/31 73:59'));    // 02/34 01:59
console.log(formatHour('12/31 00:00'));    // 12/31 00:00
console.log(formatHour('12/31 25:01'));    // 12/32 01:01
```


## コーヒー割引キャンペーン

あなたがよく利用しているコーヒーショップは本日限定であるサービスを行っています．

- `x`円のコーヒーをお買い上げした際に，次のお買い上げの値段を更に`p`% off!
- 毎回の値下げにおいて小数点以下切り捨て

あなたは値下げが累積する事に目をつけました．

コーヒーを何回も飲んでいれば，タダでコーヒーを飲めるようになるのです．

タダで頼みたいあなたは，何円払えば以後タダで注文できるのか計算したくなりました．

コーヒーの価格`x`と割引率`p`を入力して無料になるまでの支払い総額を出力する`getCostForFreeCoffee()`関数を作成してください．

`x`と`p`はこの順番に半角スペース区切りで入力されます．

```js
function getCostForFreeCoffee() {

}

console.log(getCostForFreeCoffee('300 50'));    // 596
console.log(getCostForFreeCoffee('1000 99'));    // 1010
```


## エレベーター

あなたはジーズアカデミーの用務員として，校舎に備え付けのエレベーターを管理しています．

エレベーターが一定の距離を動くと，定期点検をしなければなりません．

エレベーターの動きのログをもとに、エレベーターが何階分の距離を動いたか計算する`getElevatorMove()`関数を作成してください．

ただし，エレベーターは最初は必ず 1 階にいるものとします．

```js
function getElevatorMove() {

}

console.log(getElevatorMove('3 1 4'));    // 7
console.log(getElevatorMove('17 28 11 62 64 4 7 17'));    // 170
```
