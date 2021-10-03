# クライアント - サーバ間の通信

## サーバへデータを送る，とは？？

html ファイルや php ファイルから別の php ファイルへデータを送る．
データを受け取った php ファイルが DB への保存などの処理を実行．

データ送信には以下の 2 種類が存在する．

- GET
- POST

どちらの場合も手順は同様．

### 💡 Key Point

> 必ず送信側ファイルと受信側ファイルの 2 つでやり取りを行う．

## `GET`でのデータ送受信

### `GET`方式でデータをやり取りする場合の流れ．

#### 送信側の処理

`<form></form>`を用いてデータを送信する．必ず以下の 3 項目を設定する．

- データの送信宛先（`action="data_get_confirm.php"`）．
- データの送信方法（`method="GET"`）．
- データの項目名（`name="hoge"`）．

#### 受信側の処理

- 送信されたデータは`$_GET`変数に値が格納される．
- `$_GET`は連想配列形式となっており，送信側の`name`で設定した値がキーとなる．
- 個別の値を取り出して変数に格納すれば，後は通常の変数として処理可能．

### 送信側のコード

```php
// data_get.php

// formタグに`action`と`method`を記述
// 個々の項目（inputタグ）に`name`を指定する
<form action="data_get_confirm.php" method="GET">
  <div>
    todo: <input type="text" name="todo">
  </div>
  <div>
    deadline: <input type="date" name="deadline">
  </div>
</form>

```

### 受信側のコード

- GET で送信された情報は`$_GET`に入って送られる．
- まず「情報が受け取れているかどうか」をチェックすることが大事！！
- （情報が受け取れないと以降どうしようもない）
- `exit()`は以降の処理を中止する．

```php
// data_get_confirm.php

<?php

// 必ず最初にチェック！！内容を確認したらコメントアウトすること．
var_dump($_GET);
exit();

// キー名に送信元ファイルのname属性を指定する．
$todo = $_GET['todo'];
$deadline = $_GET['deadline'];

?>

```

### `GET`方式の特徴

- サーバから情報を取得する． URL に情報を追加して送信できる．
- データの特定（自分の名前で検索）など，少量のデータ送信に向く（URL にデータが含まれている）．
- URL にデータが含まれるため，URL をシェアするだけでデータを共有できる．

## `POST`でのデータ送受信

### `POST`方式でデータをやり取りする場合の流れ（ほとんど`GET`と同様）．

#### 送信側の処理

`<form></form>`を用いてデータを送信する．必ず以下の 3 項目を設定する．

- データの送信宛先（`action="data_post_confirm.php"`）．
- データの送信方法（`method="POST"`）．
- データの項目名（`name="hoge"`）．

#### 受信側の処理

- 送信されたデータは`$_POST`変数に値が格納される．
- `$_POST`は連想配列形式となっており，送信側の`name`で設定した値がキーとなる．
- 個別の値を取り出して変数に格納すれば，後は通常の変数として処理可能．

### 送信側のコード

```php
// data_post.php

// formタグに`action`と`method`を記述
// 個々の項目（inputタグ）に`name`を指定する
<form action="data_post_confirm.php" method="POST">
  <div>
    todo: <input type="text" name="todo">
  </div>
  <div>
    deadline: <input type="date" name="deadline">
  </div>
</form>

```

### 受信側のコード

- POST で送信された情報は`$_POST`に入って送られる．
- 以降の流れは`GET`の場合と同様．

```php
// data_post_confirm.php

<?php

// POSTの場合も必ず最初にチェック！！
var_dump($_POST);
exit();

// キー名に送信元ファイルのname属性を指定する．
$todo = $_POST['todo'];
$deadline = $_POST['deadline'];

?>

```

### `POST`方式の特徴

- サーバにデータを送信するときに使用．情報を見えないように送信する方法
- 個人情報など．（送れるデータ量が GET と比較して多い）
- ファイルを送信する場合にも使用

## 【参考】XSS : クロスサイトスクリプティング

form に悪意ある JavaScript を埋め込まれて実行される場合がある．

HTML にデータを埋め込む際に対策できる．

```php
<?php
$hoge = $_POST['hoge'];
?>

// ここからhtmlの記述
<!DOCTYPE html>
  <head>
    // 省略
  </head>
  <body>
    <p>JavaScriptが送信されると実行されてしまいます<?=$hoge?></p>
    <p>ただの文字列として処理されます<?=htmlspecialchars($hoge, ENT_QUOTES);?></p>
  </body>
</html>

```

<!-- 次の項では，データ送信機能を用いて検索処理を実装してみよう． -->

## 練習

1. `todo_get.php` と `todo_get_confirm.php` で GET 方式のデータ送受信を実装しよう．
2. `todo_post.php` と `todo_post_confirm.php` で POST 方式のデータ送受信を実装しよう．

双方とも，データを受け取ったら HTML 部分に受信内容を表示しよう．入力画面で入力した内容が受信側ファイルの画面に表示されていれば OK！
