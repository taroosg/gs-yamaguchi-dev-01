# 【おまけ】BingMapsAPI/機能追加

マップが表示されたら，マップ上にピンなどのオブジェクトを配置してみよう．

## ピンの生成

現在地をわかりやすくするピンを設定できる．

### 処理の流れ

1. 「ピンを立てる関数」を定義する．
   - ピンの色などのオプションを指定する．
   - 表示したいマップを指定する．
2. 前項で実装したマップ表示後に「ピンを立てる関数」を実行する．

### ピンを立てる関数の定義

マップ表示と同様に Microsoft が処理を用意しているため，ドキュメントに従って記述すれば OK．

本関数の中身は以下の流れ．

- 「ピンを表示したい位置の緯度」「経度」「表示したいマップ」の 3 つを入力する．
- 入力された緯度経度を Microsoft のフォーマットに変換する．
- ピンの位置と色・表示設定を指定する．
- 入力されたマップ上にピンを配置する．

```js
// geo_and_map.html

function pushPin(lat, lng, map) {
  const location = new Microsoft.Maps.Location(lat, lng);
  const pin = new Microsoft.Maps.Pushpin(location, {
    color: "navy",
    visible: true,
  });
  map.entities.push(pin);
}
```

### ピンを立てる関数の実行

マップ表示後に関数を実行する．

```js
// geo_and_map.html

function mapsInit(position) {
  const lat = position.coords.latitude;
  const lng = position.coords.longitude;
  map = new Microsoft.Maps.Map("#map", {
    center: {
      latitude: lat,
      longitude: lng,
    },
    zoom: 15,
  });
  pushPin(lat, lng, map);
}
```

## infobox の生成

infobox（吹き出し）を生成する関数を定義する．吹き出し内には任意のテキストや画像を表示することができる．

### 処理の流れ

1. 「Infobox を立てる関数」を定義する．
   - Infobox の表示内容などのオプションを指定する．
   - 表示したいマップを指定する．
2. 前項で実装したマップ表示後に「Infobox を立てる関数」を実行する．

### Infobox を生成する関数の定義

これまでと同様に Microsoft が処理を用意しているため，ドキュメントに従って記述すれば OK．

本関数の中身は以下の流れ．

- 「Infobox を表示したい位置の緯度」「経度」「表示したいマップ」の 3 つを入力する．
- 入力された緯度経度を Microsoft のフォーマットに変換する．
- Infobox の位置と表示内容を指定する．
- 入力されたマップ上に Infobox を配置する．

```js
// geo_and_map.html

function generateInfobox(lat, lng, map) {
  const location = new Microsoft.Maps.Location(lat, lng);
  const infobox = new Microsoft.Maps.Infobox(location, {
    title: `G's ACADEMY`,
    description: "JavaScript!!!",
  });
  infobox.setMap(map);
}
```

### Infobox を生成する関数の実行

マップ表示後に関数を実行する．

```js
// geo_and_map.html

function mapsInit(position) {
  const lat = position.coords.latitude;
  const lng = position.coords.longitude;
  map = new Microsoft.Maps.Map("#map", {
    center: {
      latitude: lat,
      longitude: lng,
    },
    zoom: 15,
  });
  pushPin(lat, lng, map);
  generateInfobox(lat, lng, map);
}
```

## 実行結果

マップ上にピンと Infobox が表示される．

![ピン表示結果](./img/js_api_bingmapsapi_result02.png)

## その他の機能

ここまで紹介した機能はほんの一部！！

### ドキュメントも読んでみよう！

[https://bingmapsv8samples.azurewebsites.net](https://bingmapsv8samples.azurewebsites.net)

### 山崎先生が作ったサンプル集！！（かなり参考になる！！）

[https://mapapi.org](https://mapapi.org)
