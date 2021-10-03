## nまでの和

ある2以上の整数`n`が与えられます．

1から`n`までの和を出力する`getSum()`関数を作成してください．

```js
function getSum(n) {

}

console.log(getSum(10));    // 55
console.log(getSum(99));    // 4950
```


## 数字の桁数

ある10進数の正の整数`n`が与えられます．

`n`が何桁かを数字で出力する`getNumberOfDigits()`関数を作成してください．

```js
function getNumberOfDigits(n) {

}

console.log(getNumberOfDigits(100));    // 3
console.log(getNumberOfDigits(114514));    // 6
```


## サイコロの裏面

一般的な6面サイコロの目を表す整数`n`に対し，その裏側にある目を出力する`getBackSide()`関数を作成してください．

```js
function getBackSide(n) {

}

console.log(getBackSide(1));    // 6
console.log(getBackSide(3));    // 4
```


## 単位の変換

ある正の整数`n`が入力されます．

`n`分から秒へ変換する`convertToSeconds()`関数を作成してください．

```js
function convertToSeconds(n) {

}

console.log(convertToSeconds(16));    // 960
console.log(convertToSeconds(3));    // 180
```


## 充電時間

1分間で1%の充電が可能なスマートフォンの充電器があります．

現在のスマートフォンのバッテリーの残量`n`%からこの充電器で100%まで充電するのに何分かかるかを求める`getTimeUntilFull()`関数を作成してください．

```js
function getTimeUntilFull(n) {

}

console.log(getTimeUntilFull(70));    // 30
console.log(getTimeUntilFull(25));    // 75
```


## 頭文字

あなたは半角アルファベットの苗字と名前からそれぞれ 1文字目を取りイニシャルを作ることにしました．

半角スペース区切りで苗字と名前が入力されるので，1文字目を取り "." (半角ドット)で区切った文字列を出力する`getInitialFromName()`関数を作成してください．

```js
function getInitialFromName(s) {

}

console.log(getInitialFromName('Dio Brando'));    // D.B
console.log(getInitialFromName('Pannacotta Fugo'));    // P.F
console.log(getInitialFromName('Gyro Zeppeli'));    // G.Z
```


## どれにしようかな

あなたはレストランで何を注文しようか迷っています．しかしあまり時間がないので「どれにしようかな天の神様の言うとおり」で决めてしまいましょう．

メニューの数`n`を入力し，選ばれた1から`n`までの数の一つを出力する`choiceOfGod()`関数を作成してください．

選ばれるメニューはこの文字数 21 を迷っているメニューの数で割れば求められます．ただし余りが 0 となるときはそのメニューの中で最後のものが選ばれることに注意しましょう．

```js
function choiceOfGod(n) {

}

console.log(choiceOfGod(4));    // 1
console.log(choiceOfGod(3));    // 3
```


## 日付のデータ

スペース区切りで西暦`y`，月`m`，日`d`が入力されます．

`/`区切りで文字列として出力する`formatYMD()`関数を作成してください．

ただし，西暦は4桁，月と日は2桁で出力しましょう．

```js
function formatYMD(s) {

}

console.log(formatYMD('2021 1 1'));    // 2021/01/01
console.log(formatYMD('2020 10 10'));    // 2020/10/10
console.log(formatYMD('794 11 29'));    // 0794/11/29
```


## アットマーク

半角小文字アルファベットで構成された文字列`s`が入力されます．

文字列`s`の中に含まれる`at`という文字列を全て`@`(アットマークに)置換して出力する`convertAtToAtMark()`関数を作成してください．

```js
function convertAtToAtMark(s) {

}

console.log(convertAtToAtMark('gsatcodeatquantity'));    // gs@code@quantity
console.log(convertAtToAtMark('atatatjojoatatat'));    // @@@jojo@@@
```


## 花粉症でつらい

あなたは花粉症でティッシュを毎日使っては買いに行くのを繰り返していましたが，必要なティッシュ箱の数を計算し一気に注文しようと考えました．

ティッシュ1箱が空になるまでの期間を`m`日，残りの花粉症の季節を`n`日が入力されるので，花粉症の季節が終わるまでに必要なティッシュ箱の数を求める`getNeedBox()`関数を作成してください．

```js
function getNeedBox(m, n) {

}

console.log(getNeedBox(7, 30));    // 5
console.log(getNeedBox(3, 100));    // 34
console.log(getNeedBox(7, 5));    // 1
```

