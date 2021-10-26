# 配列

## 配列（array）とは

- 複数の値に順番をつけてまとめて扱う方法．奥が深い．超強い．
- 順番を「インデックス」と呼ぶ．「0」からスタート！
  - プログラミングでは「数字は 0 から始める」（稀に例外もあり）

```js
const array = ["大吉", "中吉", "小吉", "凶", "大凶"];
alert(array[0]);
```

## 配列の作り方

下記のどちらかで作成可能．どちらでも良い（1 が多い）．

1. `[]`で囲い，要素をカンマで区切る．
2. `new Array()`の`()`内に要素をカンマ区切りで入れる．

```js
const list01 = ['月', '火', '水', '木', '金', '土', '日'];
const list02 = new Array('月', '火', '水', '木', '金', '土', '日");
console.log(list01);

```

### 💡 Key Point

> 配列はブラウザの検証画面に出力すると構造や内容が確認しやすい．

## 配列の長さ

配列の要素数を「長さ」と呼ぶ．長さは`配列名.length`で取得することができる．

繰り返し処理などで非常に有用である（後述）．

```js
console.log(list01.length); // 7
```

## 配列はいいぞ．．．

条件分岐なんていらんかったんや．．．

```js
const hands = ["グー", "チョキ", "パー"];
const randomNumber = Math.floor(Math.random() * hands.length);
const computerHand = hands[randomNumber];

console.log(computerHand);
```

結果のテーブルをつくるのもありやな．．．

```js
const resultTable = [
  ["draw", "win", "lose"],
  ["lose", "draw", "win"],
  ["win", "lose", "draw"],
];

const userHand = 0;
const computerHand = 1;

const result = resultTable[userHand][computerHand];

console.log(result);
```

## よくある配列の処理

配列には値を追加したり削除したりできる．

```js
const list01 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// 先頭に追加
list01.unshift(0); // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

// 末尾に追加
list01.push(11); // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]

// 先頭を削除
list01.shift(); // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]

// 末尾を削除
list01.pop(); // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

// 反転
list01.reverse(); // [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
```
