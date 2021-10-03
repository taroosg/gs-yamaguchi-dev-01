## お月見だんご

あなたはお月見の準備をしています．子供2人にいくつお月見だんごがほしいかをたずねますが，やんちゃな子は明らかに食べきれない数のだんごを要求してきます．

付き合いきれないのであなたは5より大きい数字を要求された場合には5個しか与えないことにしました．もちろん5以下の場合にはその数のだんごを与えます．

必要なだんごの数を求める`getNumberOfDango()`関数を作成してください．

```js
function getNumberOfDango(s) {

}

console.log(getNumberOfDango('3 50'));    // 8
console.log(getNumberOfDango('100 500'));    // 10
console.log(getNumberOfDango('2 4'));    // 6
```


## 衣替え

そろそろ衣替えのシーズンです．冬服をしまって夏服を出しましょう．

10着の服に関してそれが夏物か冬物かの情報が与えられるので，その半分 (5着) 以上が夏物になっているかどうか (なっていれば`OK`，なっていなければ`NG`) を判定する`isReadyForSummer()`関数を作成してください．

```js
function isReadyForSummer(s) {

}

console.log(isReadyForSummer('W W W W W S S S S S'));    // OK
console.log(isReadyForSummer('S S W W S W W W W W'));    // NG
console.log(isReadyForSummer('W S S S S S S S S W'));    // OK
```


## ピラミッドの作り方

あなたのクラスでは，運動会の出し物で人間ピラミッドをやることになりました．段数`n`のピラミッドを組むのに必要な人数を求める`getNumberOfHuman()`関数を作成してください．

【例】

ピラミッドの段数: 5段

1 + 2 + 3 + 4 + 5 = 15

→ 必要な人数: 15人

```js
function getNumberOfHuman(n) {

}

console.log(getNumberOfHuman(4));    // 10
console.log(getNumberOfHuman(10));    // 55
console.log(getNumberOfHuman(50));    // 1275
```


## トリック・オア・トリート

Trick or Treat! ハロウィーンのシーズンです．あなたの子供はわがままなのでお菓子といってもキャンディかチョコレートでないと満足してくれません．

文字列が与えられるので，これが`candy`か`chocolate`であれば`Thanks!`，その他の場合は `No!`という子供のリアクションを出力する`candyOrChocolate()`関数を作成してください．

```js
function candyOrChocolate(s) {

}

console.log(candyOrChocolate('chocolate'));    // Thanks!
console.log(candyOrChocolate('candy'));    // Thanks!
console.log(candyOrChocolate('pannacotta'));    // No!
```



## 11/11

今日はみんなで棒状のチョコレートお菓子を持ち寄るパーティーをします．このお菓子が合計で11本以上あればパーティーが開催できます．

このお菓子の1本は数字の`1`で表され，本数分だけ`1`が連続する文字列が与えられるので，パーティーが開催できれば`OK`，できなければ必要な本数を出力する`canParty()`関数を作成してください．

【例】

- 111111111111 → 12 ≧ 11本なのでOK

- 1111111 → 7 < 11 本なのでNG，あと 11 - 7 = 4 本必要

```js
function canParty(s) {

}

console.log(canParty('11111111111'));    // OK
console.log(canParty('1111'));    // 7
console.log(canParty('1111111111111111'));    // OK
```



## ワインのキャッチコピー

あなたはあるワインの銘柄のマーケティングを担当しています．良いキャッチコピーを考えるため，とりあえず「〜の中で最高」というフレーズを色々作ってみることにしました．

2つの文字列が与えられるので，"Best in" とそれらの文字列をすべて半角スペース区切りで結合して出力する`bestCopy()`関数を作成してください．

【例】

- hundred years → Best in hundred years
- the universe → Best in the universe

```js
function bestCopy(s) {

}

console.log(bestCopy('a decade'));    // Best in a decade
console.log(bestCopy('the world'));    // Best in the world
console.log(bestCopy('history ever'));    // Best in history ever
```


## ガチャ期待値計算

あなたがプレイしているゲームで推しキャラが実装されたので，予算と相談して引ける確率を算出したいと思いました．

推しキャラの当選確率`n`（%）と試行回数`t`（数値）を入力し，1回以上推しを引ける確率（%）を出力する`probabilityGetSSR()`関数を作成してください．

なお，出力する確率の小数点以下は四捨五入してください．

```js
function probabilityGetSSR(n, t) {

}

console.log(probabilityGetSSR(1, 100));    // 63
console.log(probabilityGetSSR(1.5, 70));    // 65
console.log(probabilityGetSSR(1, 200));    // 87
```


## 調理計画

今日は夕食当番です．コードをギリギリまで書かなければならないので，夕食の準備を開始する時間を決めたいと考えました．

夕食の時間`s`（hh:mm）と調理に要する時間`t`（分）を入力し，調理開始時間を出力する`getStartTimeForCook()`関数を作成してください．

```js
function getStartTimeForCook(s, t) {

}

console.log(getStartTimeForCook('19:00', 90));    // 17:30
console.log(getStartTimeForCook('20:00', 20));    // 19:40
console.log(getStartTimeForCook('20:30', 80));    // 19:10
```


## しかたないから全角にしてやるか

システム改修中，全角数字しか入らないデータベースを発見しました．

ユーザから送信された7桁の郵便番号を全て全角に変換して出力する`convertToUppercase()`関数を作成してください．

```js
function convertToUppercase(s) {

}

console.log(convertToUppercase('1234567'));    // １２３４５６７
console.log(convertToUppercase('1111111'));    // １１１１１１１
console.log(convertToUppercase('1145140'));    // １１４５１４０
```


## リストラ計画

チューターを解雇することになりました．現在のチューターのリストと解雇したいチューターのリストが入力されるので，残存するチューターを半角スペース区切りで出力する`fireEmployees()`関数を作成してください．

```js
function fireEmployees(employees, fireEmployees) {

}

console.log(fireEmployees('Jotaro Joseph Avdol Polnareff Tenmei Iggy', 'Avdol Tenmei Iggy'));    // Jotaro Joseph Polnareff
console.log(fireEmployees('Giorno Bucciarati Abbacchio Mista Narancia Fugo Trish', 'Bucciarati Abbacchio Narancia'));    // Giorno Mista Fugo Trish
console.log(fireEmployees('Jolyne Ermes Emporio F・F Weather Anasui', 'Jolyne Ermes F・F Weather Anasui'));    // Emporio
```
