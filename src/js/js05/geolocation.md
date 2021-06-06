# 位置情報の活用


## 位置情報とその使われ方

近年位置情報の活用幅や重要性は増しており，サービスの8割程度で利用されているとも言われている．

[参考1](https://japan.cnet.com/article/20417587/)

[参考2](https://forbesjapan.com/articles/detail/38376)

### GPSなどを用いた位置情報

- 位置情報とマップの組み合わせ
- 今まではユーザの現在地がわからなかった．
- ユーザの現在位置を視覚的に表示できるため，どこに行けばよいかがわかる．
- 地図上に店舗データなどを表示できる．
- 道を間違っても自動的に現在地からのルートが分かる

### Wifiを用いた位置情報

- 店舗のマーケティングリサーチ
- 電波強度で顧客を分類する．
    - 強ければ店内，弱ければ店外．
- 接続時間で顧客を分類する．
    - 時間が長ければ店内，短ければ店外．
    - 営業時間内なら顧客，時間外は通行人．

### ビーコンを用いた位置情報

- 店内の販促ツール．
    - 棚の近くにビーコンを設置．
    - ユーザが近づくとLINEにクーポンを配信．
- ユーザにアプリ等のツールが必要ない．
- 購入レシートを送信するとポイントが当たる．
- 再度の来店を促す．


## JavScriptでの位置情報取得

JavaScriptには標準で位置情報を取得する関数が組み込まれている．

### 種類

下記2種類の方法で位置情報を取得することができる．

|方法|概要|
|-|-|
|getCurrentPosition|処理を実行したタイミングで一度だけ位置情報を取得する．|
|watchPosition|処理を実行すると，位置情報を常に取得し続ける．<br>バッテリー消費に注意！|

### オプション

また，上記の処理を実行する際には3種類のオプションを設定することができる．

オプションはオブジェクト形式で設定し，上記処理を実行する際に読み込むことで適用される．

|オプション名|内容や設定のしかた|
|-|-|
|enableHighAccuracy|対応端末でGPSを使用するかどうかの設定．<br>`true`または`false`で指定．|
|maximumAge|指定時間以内であれば前回取得した位置情報の値を用いる．<br>ミリ秒で指定．|
|timeout|タイムアウト時間を設定する．<br>ミリ秒で指定．|

## 処理の流れとコード

位置情報を取得する処理を記述する場合には，下記の3項目が必要となるため，予め用意しておく必要がある．

1. 位置情報の取得に成功した場合に実行される関数（サンプルでは`showPosition`）．
2. 位置情報の取得に失敗した場合に実行される関数（サンプルでは`showError`）．
3. 位置情報の取得に必要なオプション（前項で紹介したもの，サンプルでは`option`）．

⚠️ 上記3項目は下記コード（位置情報取得の処理）よりも上に書いておく必要がある．

### 位置情報取得の処理

```js
// geolocation.html

navigator.geolocation.getCurrentPosition(showPosition, showError, option);

```

### 位置情報の取得に成功した場合に実行される関数

位置情報の取得に成功すると，自動的に関数の引数（下記では`position`）に位置情報が入ってくる．

まずはconsoleに出力して内容を確認しよう．

```js
// geolocation.html

function showPosition (position) {
  console.log(position);
  const lat = position.coords.latitude;
  const lng = position.coords.longitude;
  console.log(lat, lng);
};

```

### 位置情報の取得に失敗した場合に実行される関数

位置情報の取得に失敗した場合は決まったエラーが返される．

エラーには番号（`1`, `2`, `3`）が振ってあり意味が決まっているため，それぞれに対応したメッセージを表示するように記述してある．

```js
// geolocation.html

function showError (error) {
  const errorMessages = [
    '位置情報が許可されてません',
    '現在位置を特定できません',
    '位置情報を取得する前にタイムアウトになりました',
  ];
  alert(`error:${errorMessages[error.code - 1]}`);
}

```

### 位置情報の取得に必要なオプション

オブジェクトの形式で3項目を指定する．

```js
// geolocation.html

const option = {
  enableHighAccuracy: true,
  maximumAge: 20000,
  timeout: 1000000,
};

```

## 動作確認

コードが実行されると「位置情報の取得を許可するかどうか」のダイアログが表示されるため，許可する．

位置情報が取得できると，コンソール画面には以下のような情報が表示される．

位置情報は緯度経度で表現され，それぞれ`latitude`と`longitude`の値が対応する．

```js
GeolocationPosition {coords: GeolocationCoordinates, timestamp: 1622956582259}
  coords: GeolocationCoordinates
    accuracy: 200
    altitude: null
    altitudeAccuracy: null
    heading: null
    latitude: 35.69
    longitude: 139.69
    speed: null
timestamp: 1622956582259
```

## 練習

下記の処理を実装しよう！

1. 読み込み時に位置情報を取得してconsole.log()に表示しよう！
2. できる人は取得した緯度と経度をブラウザに表示しよう！

（位置情報の取得までに時間がかかることもあるので気長に待つ！）
