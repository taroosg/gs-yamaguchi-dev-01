# 位置情報の取得


位置情報

地図 / ルート検索
位置情報とマップの組み合わせ
今まではユーザの現在地がわからなかった
地図上に店舗データなどを表示
住所だけではわかりにくい
どこに行けばよいかがわかる
道を間違っても自動的に現在地からのルートが分かる

店舗のマーケティングリサーチ
電波強度を測定
強ければ店内
滞在時間で顧客を分ける
長ければ店内，短ければ店外
営業時間で調べる
営業時間内なら顧客，時間外は通行人

店内の販促ツール
棚の近くにビーコンを設置
ユーザが近づくとLINEにクーポンを配信
ユーザにアプリ等のツールが必要ない
購入レシートを送信するとポイントが当たる
再度の来店を促す

## 位置情報を取得する

種類
getCurrentPosition		 : 実行時に現在地を取得する．
watchPosition			 : 実行したら位置情報を取得し続ける．
（watchPosition）はバッテリー消費に注意！！
オプション
enableHighAccuracy		 : 対応端末でGPSを使用
maximumAge			 : 指定時間以内であれば前回の値を用いる
timeout				 : タイムアウト時間を設定


```js
// ()内には「成功時の関数」「失敗時の関数」「オプション」の順に記述する．

navigator.geolocation.getCurrentPosition(showPosition, showError, option);

```

```js
// 成功時の関数（位置情報を表示する）

function showPosition(position) {
  const lat = position.coords.latitude;
  const lng = position.coords.longitude;
  console.log(lat, lng);
}
```

```js
// 失敗時の関数（エラーを表示する）

function showError(error) {
  const errorMessages = [
    '位置情報が許可されてません',
    '現在位置を特定できません',
    '位置情報を取得する前にタイムアウトになりました',
  ];
  alert(`error:${errorMessages[error.code - 1]}`);
}

```

```js
const option = {
  enableHighAccuracy: true,
  maximumAge: 20000,
  timeout: 1000000,
};
```

### 動作確認

コンソール画面には以下のような情報が表示される．

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

練習

下記の処理を実装しよう！
読み込み時に位置情報を取得してconsole.log()に表示しよう！
できる人は取得した緯度と経度をブラウザに表示しよう！
（位置情報の取得までに時間がかかることもあるので気長に待つ！）
