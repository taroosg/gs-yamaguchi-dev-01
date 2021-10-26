# オブジェクト

## オブジェクトとは

- 配列と同様に複数の値を管理する方法
- 配列の「インデックス」に対して「キー」「バリュー」で管理．

```js
const jojo01 = {
  number: 1,
  title: "ファントムブラッド",
  hero: "ジョナサン・ジョースター",
  rival: "ディオ・ブランドー",
  sound: "メメタァ",
};
console.log(jojo01.sound);
console.log(jojo01["sound"]);
```

## 配列とオブジェクトの組み合わせ

この形は非常に多い．今後もたくさん出てくるので慣れておくことを推奨するッ！！

```js
const jojo = [
  {
    number: 1,
    title: "ファントムブラッド",
    hero: "ジョナサン・ジョースター",
  },
  {
    number: 2,
    title: "戦闘潮流",
    hero: "ジョセフ・ジョースター",
  },
  {
    number: 3,
    title: "スターダストクルセイダース",
    hero: "空条承太郎",
  },
];

console.log(jojo[0].title); // ファントムブラッド
console.log(jojo[2].hero); // 空条承太郎
```

## 練習

配列の練習

- `list/array.html`

オブジェクトの練習

- `list/object.html`

<!-- 上記が楽勝な人

- `list/challenge.html` -->
