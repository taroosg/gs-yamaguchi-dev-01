## ゾロ目の日付

11月11日が迫るある日，あなたはゾロ目の日付を判定するプログラムを作成することにしました．

ゾロ目の日とはある日付に対して月と日に含まれる全ての桁の数字が同じものを指します．
スペース区切りで月と日が与えられるのでゾロ目の日であれば`Yes`そうでなければ`No`と出力する`isSingleNumber()`関数を作成してください．

例えば入力例1では11月1日が以下のように与えられます．

`11 1`

この場合，月と日ともに1のゾロ目なので

`Yes`

と出力して下さい．

```js
function isSingleNumber(s) {

}

console.log(isSingleNumber('11 1'));    // Yes
console.log(isSingleNumber('11 11'));    // Yes
console.log(isSingleNumber('12 11'));    //  No
```


## 花見の準備

あなたはお花見の準備のためにレジャーシートを買うことにしました．

レジャーシートの質に興味のないあなたは最も面積あたりの価格の安いレジャーシートを探すため，プログラムを書くことにしました．

2つのレジャーシートの横の長さ`x`, 縦の長さ`y`, 価格`p` がスペース区切りで与えられます．1つ目のレジャーシートのデータと2つ目のレジャーシートのデータはカンマ区切りとなります．

最も面積あたりの価格の安いレジャーシートの`x`, `y`, `p`をスペース区切りで出力する`judgeCheapSheet()`関数を作成してください．
ただし，面積あたりの価格が同じ場合は`DRAW`と出力してください．

```js
function judgeCheapSheet(s) {

}

console.log(judgeCheapSheet('5 18 1000,12 21 3000'));    // 5 18 1000
console.log(judgeCheapSheet('5 5 1800,5 10 3600'));    // DRAW
```


## 下一桁はいくつ

あなたは5つの数字を足し算するプログラムを作成しています．しかし，出力したい数字は下一桁のみです．

5つの数字がスペース区切りで入力されるので，全てを足した結果の下一桁を出力する`getLastNumber()`関数を作成してください．

例えば以下のような入力の場合

`1 9 8 9 12`

足すと39となりますが`9`と下一桁のみ出力します．

```js
function getLastNumber(s) {

}

console.log(getLastNumber('1 9 8 9 12'));    // 9
console.log(getLastNumber('1 1 1 1 6'));    // 0
```


## 門松の作成

あなたはお正月に向けて門松を作ることにしました．門松は3本の竹からなり，それぞれ竹の長さは`3:5:7`の比率で作る習わしとなっています．

最も短い竹の長さが与えられるので， 3本の竹に切断し門松を作るために必要な竹の長さを出力する`getAllLength()`関数を作成してください．この時切断面は竹に対して垂直に切られるものとします．

```js
function getAllLength(n) {

}

console.log(getAllLength(60));    // 300
console.log(getAllLength(9));    // 45
```


## 禁止ワード

あなたは禁止ワードが含まれるかどうかを判定するプログラムを作成しています．

禁止ワード`w`と判定する文字列`s`が改行区切りで順に与えられるので`s`に`w`が含まれている時は`NG`それ以外の場合は文字列`s`をそのまま出力する`hasNgWord()`関数を作成してください．

```js
function hasNgWord(s) {

}

console.log(hasNgWord('ngword thisisngword'));    // NG
console.log(hasNgWord('ngword gsprogramming'));    // gsprogramming
```


## 洗濯物と砂ぼこり

あなたは洗濯物を干すかどうか，その日の気温と湿度で決めることにしました．

暖かくて乾燥してる日を選んで干したいところですが，家の向には公園があり，そういった日は砂ぼこりが舞ってしまいます．

そこであなたは干すためのルールを決めました．

気温が25℃以上の日，もしくは湿度が40%以下の日は干します．それ以外の日は干しません．
ただし，上記の干す条件を満たす日のうち，気温が25℃以上かつ，湿度40%以下の日は砂ぼこりが舞うので干しません．

その日の気温と湿度が与えられるので，干すかどうか判断（`Yes`か`No`を出力）する`canDry()`関数を作成してください．

```js
function canDry(s) {

}

console.log(canDry('25 50'));    // Yes
console.log(canDry('10 20'));    // Yes
console.log(canDry('20 50'));    // No
```


## カード並べ

フライト中に退屈してしまったあなたは，持っているトランプを使用した簡単な遊びを考えました．

この遊びでは1から9までの数字のカードのみを4枚使用します．
ただし，この4枚の中で同じ数値のカードが重複する事もあります．

ルールは以下の通りです．

4枚のカードを横に並べます．
左から2枚のカード，右から2枚のカードをそれぞれ2ケタの整数とみなし，和を計算します．
あらゆる並べ方を試し，和の最大値（最大スコア）を求めます．

カード4枚に書かれた数が与えられるので，最大スコアを出力する`getBestScore()`関数を作成してください．
入力例1の2, 9, 3, 8の4枚を使う場合，最大値175が最大スコアとなります．

```js
function getBestScore(s) {

}

console.log(getBestScore('2 9 3 8'));    // 175
console.log(getBestScore('7 8 7 7'));    // 164
```


## ログのフィルター

あなたはサーバ管理者です． 日々洪水のように流れるログを追っています．

とうとう自分の目と頭では処理しきれない量になってしまったため，プログラムを作って，重要な文字列を含むログだけ抽出する事にしました．

重要な文字列とログ（半角スペース区切り文字列）がカンマ区切りで入力されるので，重要な文字列が入ったログのみを半角スペース区切りで出力する`filterLogByKeyword()`関数を作成してください．

ログ内に重要な文字列が含まれるデータがない場合な`None`と出力しましょう．

```js
function filterLogByKeyword() {

}

console.log(filterLogByKeyword('gs,gsacademytokyo javascript gsacademyfukuoka gsbase'));    // gsacademytokyo gsacademyfukuoka gsbase
console.log(filterLogByKeyword('script,javascript typescript googleappscript java'));    // javascript typescript googleappscript
console.log(filterLogByKeyword('dio,Giorno Bucciarati Abbacchio Mista Narancia Fugo Trish'));    // None
```


## メールアドレス認証

ある開発者はベータテストユーザーを，メールアドレス登録によって受け付けることにしました．その際，ユーザーのメールアドレスが有効なものなのかをチェックするプログラムが必要になります．

あるメールアドレスを受け取るので，それが正しいものであれば`true`を，そうでなければ`false`を返す`isValidEmail()`関数を作成してください．ここでの正しいアドレスというのは以下の4つの条件を満たすものを指します．

- 「@」から始まらないこと
- スペースがないこと
- 「@」を 1 つのみ含んでいること
- 「@」の後に「.」があること

```js
function isValidEmail() {

}

console.log(isValidEmail('ccc@aaa.com'));    // true
console.log(isValidEmail('c@cc@aaa.com'));    // false
console.log(isValidEmail('cc c@aaa.com'));    // false
console.log(isValidEmail('cc.c@aaacom'));    // false
console.log(isValidEmail('cc.c@aaa.com'));    // true
console.log(isValidEmail('@aaa.com'));    // false
```


## フィボナッチ数列

自然界に多くみられる数列として，フィボナッチ数列という数列があります．フィボナッチ数列は以下の公式で表されます．

【フィボナッチ数列とは】

- f(0) = 0
- f(1) = 1
- f(n) = f(n-2) + f(n-1)       (ただし，n >= 2であることが条件)

【具体例】

- f(2) = 0 + 1 = 1
- f(3) = 1 + 1 = 2
- f(4) = 1 + 2 = 3
- f(5) = 2 + 3 = 5

ある青年は，手動で50番目まで計算したところで，この計算を手動で無限に続けるのは無理だと思い，これを100番目でも10000番目でも瞬時に計算できるプログラムを作りたいと考えました．

青年を助けるための`getFibonacciNth()`関数を作成してください．

数が大きくなると計算に時間を要するので，実装を工夫することをオススメします．

```js
function getFibonacciNth() {

}

console.log(getFibonacciNth(1));    // 1
console.log(getFibonacciNth(5));    // 5
console.log(getFibonacciNth(10));    // 55
console.log(getFibonacciNth(90));    // 2880067194370816120
```

