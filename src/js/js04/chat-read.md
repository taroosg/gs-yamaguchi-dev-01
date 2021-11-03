# データのリアルタイム取得と画面表示

## 保存されているデータの扱い

Firestore ではデータの取得方法はいくつか用意されているが，最大の特徴は「データベースの変更を検知して自動的にデータを取得できる」ことである．

（本来はサーバ側の言語での実装が必要であり，難易度も高い．WebSocket などの実装が必要）

## 処理の流れ

流れは送信と比較して複雑となる．理由は以下のとおり．

- 動作のタイミングがつかみにくい．
- 取得したデータが非常に複雑な状態．
- 必要な 3 項目を取得するために Firestore 側で用意された関数を使用する必要がある．

## データの取得

まずは Firestore 上に保存されているデータを取得して console に出力する．

- データに変更（追加，更新，削除など）が生じたタイミングで実行される`onSnapshot()`を使用する．
- `onSnapshot()`はデータベース上でデータの変更が発生したタイミングで`{}`内の処理を実行する．
- Firestore 上に保存されているデータは`querySnapshot.docs`に入っている．

```js
// chatapp.html

// 🔽 `onSnapshot`を追記
import {
  getFirestore,
  collection,
  addDoc,
  serverTimestamp,
  onSnapshot,
} from "https://www.gstatic.com/firebasejs/9.0.2/firebase-firestore.js";

// 省略

// データ取得処理
onSnapshot(collection(db, "chat"), (querySnapshot) => {
  console.log(querySnapshot.docs);
});
```

## データの取り出し

上記`querySnapshot.docs`は非常に複雑な形となっており，このまま扱うことは難しい．

そのため，必要なデータのみ抽出した「オブジェクト形式の配列」に変換する．

1. 空の配列を準備．
2. `querySnapshot.docs`に対して繰り返し処理を用いて各要素に対して，
   - `.id`でドキュメント ID（名前）を取得する．
   - `.data()`でドキュメント中身（3 項目）を取得する．
3. 上記のデータのみを 1 で用意した配列に追加．

```js
// chatapp.html
// 前項の`console.log()`下に記述

const dataArray = [];
querySnapshot.docs.forEach(function (doc) {
  const data = {
    id: doc.id,
    data: doc.data(),
  };
  dataArray.push(data);
});

console.log(dataArray);
```

### 💡 Key Point

> 難しい形式のデータは変換して「自分が慣れている形式」に変換すると扱いやすい．

## 画面表示するためのタグ生成

必要な情報のみを抽出した配列が作成できたため，この配列から画面表示用のタグを作成する．

前項で作成した`dataArray`を基にして，

1. 空の配列を準備する．
2. `dataArray`に繰り返しを用い，各要素をタグの形にする．
3. 繰り返し処理終了後に指定した id 部分に出力する．

```js
// chatapp.html
// 前項の`console.log()`下に記述

const tagArray = [];
dataArray.forEach(function (data) {
  tagArray.push(`
    <li id="${data.id}">
      <p>${data.data.name} at ${data.data.time}</p>
      <p>${data.data.text}</p>
    </li>
  `);
});

$("#output").html(tagArray);
```

## 動作確認

上記のコードを記述すると「Firestore 上でデータが変更されたタイミング」で`{}`内の処理が実行され，最新のデータが画面に反映される．

![データ取得](./img/20210616152526.png)

また，「Firestore 上でデータが変更されたタイミング」で動作するため，複数タブで片方だけ操作した状態でもう片方の動作を確認することができる．

### 💡 Key Point

> - `onSnapsyot` が動くタイミングを把握せよ！
> - Firestore から取ってきたデータを使用する処理を書く場合は全て `onSnapsyot` の `{}` 内に書く必要がある！

## 練習

下記の順番でデータの表示を実装しよう．

1. データ本体を取得．
2. データから必要なものだけを抽出．
3. 抽出したデータからタグを作成．
4. タグを画面に表示．

入力フォームからデータを送信し，一覧に追加されれば OK．
