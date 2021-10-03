## カウントダウン
正整数`n`が入力されるので，`n`から1まで1ずつカウントダウンする`countDown()`関数を作成してください．

例えば

`3`

と入力された場合

`3 2 1`

と出力してください．

```js
function countDown(n) {

}

console.log(countDown(3));     // 3 2 1
console.log(countDown(10));    // 10 9 8 7 6 5 4 3 2 1
```


## N文字目まで出力

半角アルファベットで構成された文字列`s`と正の整数`n`入力されます．

1文字目から`n`文字目までを出力する`getOneToN()`関数を作成してください．

例えば

`abcdefg`と`4`

と入力された場合

`abcd`

と出力して下さい．

```js
function getOneToN(s, n) {

}

console.log(getOneToN('aabbccdd', 5));    // aabbc
console.log(getOneToN('gsacademyfukuoka', 9));    // gsacademy
```


## 最大と最小

5個の数字 `n_1`, `n_2`, `n_3`, `n_4`, `n_5` が半角スペース区切りで与えられます．

それらの数字の最大の数字，最小の数字を半角スペース区切りで出力する`getMaxAndMin()`関数を作成してください．

例えば

`9 12 3 6 10`

と入力された場合

`12 3`

と出力してください．

```js
function getMaxAndMin(s) {

}

console.log(getMaxAndMin('9 12 3 6 10'));    // 12 3
console.log(getMaxAndMin('1 1 2 2 3'));    // 3 1
console.log(getMaxAndMin('5 9 -1 10 2'));    // 10 -1
```


## 文字列からN番目

半角アルファベット文字列`s`と整数`n`が入力されます．

文字列`s`の1番左の文字を1文字目とし`n`文字目のアルファベットを出力する`getNthChar()`関数を定義してください．

例えば

`gsacademy`と`3`

と入力された場合

`a`

と出力して下さい．

```js
function getNthChar(s, n) {

}

console.log(getNthChar('gsacademy', 3));    // a
console.log(getNthChar('abcdefg', 5));    // e
console.log(getNthChar('qwertyu', 1));    // q
```


## 文字列の一致

文字列`s`と文字列`t`が半角スペース区切りで入力されます．

`s`と`t`が完全一致していれば「Yes」，それ以外は「No」と出力する`isEqual()`関数を作成してください．

```js
function isEqual(s, t) {

}

console.log(isEqual('gsacademy', 'gsacademy'));    // Yes
console.log(isEqual('JavaScript', 'ジャバスク'));    // No
console.log(isEqual('aaaaa', 'aaaaaa'));    // No
```


## Aの個数

半角アルファベットで構成された文字列`s`が与えられます．

`s`に含まれる半角アルファベット「A」の数を出力する`getNumberOfA()`関数を作成してください．

```js
function getNumberOfA(s) {

}

console.log(getNumberOfA('GSACADEMY'));    // 2
console.log(getNumberOfA('aAaAaA'));    // 3
console.log(getNumberOfA('JavaScript'));    // 0
```


## 表面積の計算

立方体の体積を求めましょう．

一辺の長さ`a`が入力されるので，立方体の表面積を出力する`getSurfaceArea()`関数を作成してください．

```js
function getSurfaceArea(a) {

}

console.log(getSurfaceArea(4));    // 96
console.log(getSurfaceArea(1));    // 6
```


## 三角形の内角の和

平面上の三角形の2つの角の角度`a`, `b`を入力し，残りの1つの角の角度を出力する`getAngle()`関数を作成してください．

```js
function getAngle(a, b) {

}

console.log(getAngle(30, 90));    // 60
console.log(getAngle(45, 45));    // 90
```


## 数字の出力

ある正の整数`n`（最大2桁）が入力されます．

`n`を0埋め3桁で出力する`zeroPadding3()`関数を作成してください．

例えば以下のような入力の場合

`98`

以下のように出力して下さい

`098`

```js
function zeroPadding3(n) {

}

console.log(zeroPadding3(98));    // 098
console.log(zeroPadding3(2));    // 002
```


## 一週間の予定

あなたは1週間を全て休みにするために有給を申請することにしました．もともと決まっている休みもあります．

半角スペース区切りで7日間の休みが，休みならば「yes」，休みでなければ「no」と入力されます．

有給申請しなくては行けない日数を出力する`getPaidHolidays()`関数を作成してください．

```js
function getPaidHolidays(s) {

}

console.log(getPaidHolidays('yes yes yes yes no no yes'));    // 2
console.log(getPaidHolidays('yes no no no no no yes'));    // 5
```

