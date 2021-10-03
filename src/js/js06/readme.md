# JavaScript 100本ノック

## 目的

- JavaScriptの初歩的な処理をひたすら繰り返すことで定着を狙う．
- 初歩的な処理を組み合わせ，やや複雑な処理を自身で組み立てられるようにする．

## 進め方

- 1から順番に挑戦しよう．

## 注意点

- いろいろなところのコードを参考にしているため，転載は控えましょう．


## 【例題】長方形の面積

### 問題

長方形の長辺`a`(mm，自然数)と短辺`b`(mm，自然数)が入力されると面積(mm2，自然数)を出力する関数`calculateArea()`関数を作成してください．

入力される値（a, b）は必ず自然数であるものとし，自然数以外の値が入力される場合を考慮する必要はない（以降の問題でも同様）．

```js
function calculateArea(a, b){
  // ここに処理を記述！
}

console.log(calculateArea(2, 5));     // 10
console.log(calculateArea(10, 10));   // 100
```


### 回答例

下記のように記述して動作確認を行い，想定している値が出力されていればOK！

```js
function calculateArea(a, b){
  return a * b;
}

console.log(calculateArea(2, 5));     // 10
console.log(calculateArea(10, 10));   // 100
```

上記の要領で関数を作成しよう( ` ･ω･)b


