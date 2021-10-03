## 数の比較
整数の入力値`a`と`b`を比較し大きい方の値を出力する`compareNumbers()`関数を作成してください．aとbが等しい場合は`eq`と出力して下さい．

```js
function compareNumbers(a, b) {

}

console.log(compareNumbers(2, 5));    // 5
console.log(compareNumbers(10, 9));   // 10
console.log(compareNumbers(2, 2));    // eq
```


## 単位の計算
距離`n`とその単位`s`が入力されるので，すべての距離を`mm`に換算し数値で出力する`convertToMm()`関数を作成してください．

入力される距離の単位は km, m, cm の3種類で，それぞれ以下のように換算出来ます．

- 1km = 1000 m
- 1m = 100 cm
- 1cm = 10 mm

```js
function convertToMm(n，s) {

}

console.log(convertToMm(1, 'km'));    // 1000000
console.log(convertToMm(54, 'km'));   // 54000000
console.log(convertToMm(2, 'cm'));    // 20
```


## 奇数か偶数か
正の整数`n`が入力されるので，`n`奇数ならば`odd`偶数ならば`even`と出力する`oddOrEven()`関数を作成してください．

```js
function oddOrEven(n) {

}

console.log(oddOrEven(4));    // even
console.log(oddOrEven(5));    // odd
console.log(oddOrEven(2));    // even
```


## 西暦の計算
2つの西暦`a`と`b`を入力し，`a`から`b`が何年間あるか出力する`calculateYears()`関数を作成してください（`a < b`とする）．

```js
function calculateYears(a, b) {

}

console.log(calculateYears(1990, 2014));    // 24
console.log(calculateYears(1999, 2000));    // 1
console.log(calculateYears(794, 1192));    // 398
```


## 何番目？

以下のような A〜Z (半角英字大文字) の中から1文字入力されます．

ABCDEFGHIJKLMNOPQRSTUVWXYZ
A を 1番目としてアルファベット順で何番目かを出力する`judgeTh()`関数を作成してください．

例えば`C`を入力した場合は`3`と出力して下さい．

```js
function judgeTh(c) {

}

console.log(judgeTh('C'));    // 3
console.log(judgeTh('X'));    // 24
```


## 絶対値

`-100`から`100`までの整数`n`が与えられるので，絶対値を出力する`getAbs()`関数を作成してください．

```js
function getAbs(n) {

}

console.log(getAbs(-10));    // 10
console.log(getAbs(15));     // 15
console.log(getAbs(0));      // 0
```


## 割り算
整数`m`と`n`を入力し，`m`を`n`で割り算した商と余りを半角スペース区切りの文字列で出力する`getQuotientAndSurplus()`関数を作成してください．

```js
function getQuotientAndSurplus(m, n) {

}

console.log(getQuotientAndSurplus(10, 3));    // 3 1
console.log(getQuotientAndSurplus(12, 14));    // 0 12
```


## 小文字を大文字に

半角アルファベットの小文字で構成された長さ`n`の文字列`s`が与えられます．

文字列`s`を大文字に変換して出力する`convertToUppercase()`関数を作成してください．

```js
function convertToUppercase(s) {

}

console.log(convertToUppercase('gsacademy'));    // GSACADEMY
console.log(convertToUppercase('abcdefghijklmnopqrstuvwxyz'));    // ABCDEFGHIJKLMNOPQRSTUVWXYZ
```


## 掛け算のリスト

正の整数1から9に整数nをそれぞれを掛けた数を半角スペース区切りで出力する関数`createList()`関数を作成してください．

例えばn=2の場合は

`2 4 6 8 10 12 14 16 18`

となります．

```js
function createList(n) {

}

console.log(createList(2));    // 2 4 6 8 10 12 14 16 18
console.log(createList(3));    // 3 6 9 12 15 18 21 24 27
console.log(createList(5));    // 5 10 15 20 25 30 35 40 45
```


## 等差数列

以下のような数列を考えます．

`5 8 11 14 17 20 23 26 29 32`

最初の数字が5で，3ずつ増加していく事がわかります．
一般的にこれを初項5，公差3の等差数列といいます．

このような数列を出力するプログラムを作りましょう．

初項`m`と公差`n`が入力し，10番目までの数字をスペース区切りで出力する`createSequence()`関数を作成してください．

```js
function createSequence(m, n) {

}

console.log(createSequence(3, 3));    // 3 6 9 12 15 18 21 24 27 30
console.log(createSequence(5, 10));    // 5 15 25 35 45 55 65 75 85 95
console.log(createSequence(1, 3));    // 1 4 7 10 13 16 19 22 25 28
```
