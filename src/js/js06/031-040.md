## 本棚選び

あなたは新しい本棚を買おうと検討しています．そこで，既に持っている本の幅などから収まるか概算することにしました．

持っている本の幅を合計したもの`n`(cm)，検討している本棚の段数`d`，本が収まる幅`e`(cm)がそれぞれ半角スペース区切りで入力し，本が収まるかどうかを`OK`または`NG`で出力する`canStoreBooks()`関数を作成してください．

概算なので本それぞれの違い1段に収まるかは考えないことにします．

例えば，本の幅を合計したものが400(cm)，検討している本棚の段数が5，本が収まる幅が85 (cm)の場合は以下の様な入力になり，

`400 5 85`

各段の幅を合計したものは85かける5で425(cm)となり，400(cm)の本は収まるので以下のように出力して下さい．

`OK`

収まらない場合は`NG`を出力してくだだい．

```js
function canStoreBooks(s) {

}

console.log(canStoreBooks('400 5 85'));    // OK
console.log(canStoreBooks('500 4 70'));    // NG
```


## 試合の回数

あなたは1対1で戦う競技の大会を開くことにしました．

`n`人の選手で総当り対戦を行う場合，対戦の回数を出力する`calculateNumberOfGames()`関数を作成してください．

総当り戦では`n`人がそれぞれ自分自身以外と対戦します．

```js
function calculateNumberOfGames(n) {

}

console.log(calculateNumberOfGames(4));    // 6
console.log(calculateNumberOfGames(10));    // 45
```


## 連休の天気

あなたは7日間の連休をもらいましたが，降水確率が30%以下ならば外に出掛ける事に決めました．

7日間の降水確率(%)が半角スペース区切りで入力されるので，出掛ける日数の合計を出力する`daysOfGoOut()`関数を作成してください．

```js
function daysOfGoOut(s) {

}

console.log(daysOfGoOut('13 0 15 30 89 100 30'));    // 5
console.log(daysOfGoOut('0 14 18 22 0 2 4'));    // 7
console.log(daysOfGoOut('99 99 99 99 99 99 99'));    // 0
```


## 正三角形かどうか

あなたは，3つの辺の長さが分かっている三角形が正三角形なのかを判別しようとしています．

3つの辺の長さ a, b, c が半角スペース区切りで与えられるので正三角形なら`YES`, 正三角形でなければ`NO`と出力する`isEquilateralTriangle()`関数を作成してください．

```js
function isEquilateralTriangle(s) {

}

console.log(isEquilateralTriangle('10 10 10'));    // yes
console.log(isEquilateralTriangle('3 4 5'));    // No
```


## 天気の表示

あなたは0% 〜 100%の降水確率を得て，その数値から天気を文字列で表示をしようと考えました．

表示のルールは以下のよう定めました．

- 降水確率が 0 % 以上 30 % 以下ならば`sunny`
- 降水確率が 31 % 以上 70 % 以下ならば`cloudy`
- 降水確率が 71 % 以上ならば`rainy`

降水確率`n`(%)が与えられるので上のルールに従って文字列を出力する`showWeather()`関数を作成してください．

```js
function showWeather(n) {

}

console.log(showWeather(31));    // cloudy
console.log(showWeather(2));    // sunny
console.log(showWeather(71));    // rainy
```


## はじめまして

はじめましてのあいさつをしましょう．

名前が文字列`s1`で，性別が文字列`s2`(男性は`M`, 女性は`F`) で与えられます．
これに対し，男性なら`Hi, Mr.〇〇(名前)`と，女性なら`Hi, Ms.〇〇(名前)`と出力する`greet()`関数を作成してください．

```js
function greet(s1, s2) {

}

console.log(greet('Stroheim', 'M'));    // Hi, Mr.Stroheim
console.log(greet('Trish', 'F'));    // Hi, Ms.Trish
```


## 通知票

ジーズ中学校ではこれまで5~1の数字で成績をつけていましたが，英語教育に力を入れるため今年度からA~Eのアルファベットで成績をつけることにしました．

すでに成績を数字でつけてしまったあなたはあわててアルファベットに変換することにしました．

【変換ルール】
- 5 -> A
- 4 -> B
- 3 -> C
- 2 -> D
- 1 -> E

5教科について数字の評価が入力されるので，アルファベットの評価を出力する`convertNumberToAlphabet()`関数を作成してください．

```js
function convertNumberToAlphabet(s) {

}

console.log(convertNumberToAlphabet('53342'));    // ACCBD
console.log(convertNumberToAlphabet('22222'));    // DDDDD
console.log(convertNumberToAlphabet('51111'));    // AEEEE
```


## 不思議なタマゴ

持ったまま一定の距離を歩くと孵化する不思議なタマゴ（1km, 2km, 5km）があります．

あなたはこのタマゴをなるべくいっぺんに孵化させようと思い，3つをまとめて持っていくことにしました．

これらをすべて孵化させるのに最低限必要な歩行距離を求める`getNumberOfSteps()`関数を作成してください．

```js
function getNumberOfSteps(s) {

}

console.log(getNumberOfSteps('1 2 5'));    // 5
console.log(getNumberOfSteps('2 5 5'));    // 5
console.log(getNumberOfSteps('1 2 1'));    // 2
```

## 台風の間隔

あなたは気象庁のデータ分析の担当者で，8月の台風の上陸の間隔についてのデータを作るよう求められました．

サンプルとなる5個の台風について上陸した日が与えられるので，それぞれ (2個目以降) について直前の上陸日との間隔日数を出力する`getInterval()`関数を作成してください．

```js
function getInterval(s) {

}

console.log(getInterval('5 8 19 25 31'));    // 3 11 6 6
console.log(getInterval('2 3 7 9 28'));    // 1 4 2 19
```


## ◯◯の秋

あなたは，「わたしの秋は◯◯の秋」というアンケートの集計を任されました．

アンケートの回答はまちまちで，「◯◯の秋」と書く人もいれば「◯◯」の部分だけ書く人もいます．これでは不便なのでまず「◯◯」の部分だけを取り出す`getAutumn()`関数を作成してください．

```js
function getAutumn(s) {

}

console.log(getAutumn('codenoaki'));    // code
console.log(getAutumn('dokusyo'));    // dokusyo
console.log(getAutumn('javascriptnoaki'));    // javascript
```

