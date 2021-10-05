# CSS / レイアウト

## よくあるレイアウト

|          |                             |
| -------- | --------------------------- |
| 横並び   | HTML は縦並びがデフォルト． |
| 左右中央 | HTML は左揃えがデフォルト． |
| 上下中央 | HTML は上揃えがデフォルト． |

## float．．？

float を使うと要素を横並びにできる．．．が．．．

![float例](./img/html_css_float.png)

[参考：https://gray-code.com/html_css/release-float-by-clearfix/](https://gray-code.com/html_css/release-float-by-clearfix/)

**ものッ！すごくッ！！めんどくさいィィッッッ！！！！**

## FlexBox が全てを解決するッ！！

- 横並び
- 左右中央揃え
- 上下中央揃え

### HTML のイメージ

下記のような要素を想定する（主な部分のみ記述）．

```html
<div class="l_box">
  <div class="s_box sienna"></div>
  <div class="s_box firebrick"></div>
  <div class="s_box maroon"></div>
  <div class="s_box darkmagenta"></div>
  <div class="s_box indigo"></div>
</div>
```

↓ 画面上はこんな感じ

![初期状態](./img/html_css_flex_unset.png)

### 横並び

`display: flex;` を記述！

- HTML は縦並びがデフォルト．
- `display: flex;` を使用すると横並びにできる！

> **💡 Point**
>
> `display: flex;` に関連する CSS は「レイアウトを制御したい要素の外側の要素」に記述する！

```css
.l_box {
  display: flex;
}
```

![横並び](./img/html_css_flex_flex.png)

### 左右中央揃え

`justify-content: center;` を記述！

- HTML は左揃えがデフォルト．
- `justify-content: center;` を使用すると左右中央揃えにできる！

> **💡 Point**
>
> `display: flex;` は常に記述する必要あり！

```css
.l_box {
  display: flex;
  justify-content: center;
}
```

![左右中央](./img/html_css_flex_justify_center.png)

### 上下左右中央揃え

`align-items: center;` を記述！

- HTML は上揃えがデフォルト．
- `align-items: center;` を使用すると上下中央揃えにできる！

```css
.l_box {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

![上下左右中央](./img/html_css_flex_align_center.png)

### 縦並びが良い場合

`flex-direction: column;` を記述！

- flex は横並びがデフォルト．
- `flex-direction: column;` を使用すると縦横の並び方を制御できる！

```css
.l_box {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
```

![縦並び](./img/html_css_flex_column.png)

### 【参考】いい感じに並べたいとき

均等な感じにしたい場合にも設定できる．

↓ 端に寄せつつ均等に並べる `space-between`

```css
.l_box {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

![between](./img/html_css_flex_justify_between.png)

↓ 均等に余白をつくって並べる `space-evenly`

```css
.l_box {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
```

![evenly](./img/html_css_flex_justify_evenly.png)

## 練習

**FlexBox を駆使して横並び部分を実装しよう！**

ヒント！！

横並びの幅を均等にしたい！

- 横に並んでいる div の width を「50%」にしよう！

画像がはみ出す！

- 画像の width を「100%」に設定すると箱の幅に合わせてくれる！
- 高さが足りないときは height も「100%」！
- 画像の比率がおかしいときは「object-fit」でググれ！

![flex実装後](./img/html_css_work_flex.png)
