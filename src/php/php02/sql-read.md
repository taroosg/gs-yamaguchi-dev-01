# PHP と DB の連携（データ参照処理）

## 必要なファイル

- `todo_read.php`：DB からデータを取得してデータの一覧画面を作成する．

## 処理の流れ

1. 表示ファイル（`todo_read.php`）へアクセス時，DB 接続する．
2. データ参照用 SQL 作成 → 実行．
3. 取得したデータを HTML に埋め込んで画面を表示．

※必要に応じて，並び替えやフィルタリングを実施してみよう．

## DB データ作成処理の実装

### DB 接続

新規データ作成の場合と同様の処理（DB 名の設定を忘れずに！）．

```php
// todo_read.php

$dbn ='mysql:dbname=YOUR_DB_NAME;charset=utf8;port=3306;host=localhost';
$user = 'root';
$pwd = '';

try {
  $pdo = new PDO($dbn, $user, $pwd);
} catch (PDOException $e) {
  echo json_encode(["db error" => "{$e->getMessage()}"]);
  exit();
}

```

### SQL 作成&実行

データ作成処理と同様に SQL を記述して実行する．今回は「ユーザが入力したデータ」を使用しないのでバインド変数は不要．

また，`$status`には実行結果が入るが，この時点ではまだデータ自体の取得はできていない点に注意．

```php
// todo_read.php

$sql = 'SELECT * FROM todo_table';
$stmt = $pdo->prepare($sql);

try {
  $status = $stmt->execute();
} catch (PDOException $e) {
  echo json_encode(["sql error" => "{$e->getMessage()}"]);
  exit();
}

```

### SQL 実行後の処理

SQL が正常に実行された場合は以下の流れで処理が実行される．

- `fetchAll()`関数でデータ自体を取得する．
- 繰り返し処理を用いて，取得したデータから HTML タグを生成する．
- （HTML 内の任意の位置に作成したタグを設置

```php
// todo_read.php

// SQL実行の処理

$result = $stmt->fetchAll(PDO::FETCH_ASSOC);
$output = "";
foreach ($result as $record) {
  $output .= "
    <tr>
      <td>{$record["deadline"]}</td>
      <td>{$record["todo"]}</td>
    </tr>
  ";
}

```

### HTML にタグを埋め込み

```php
// todo_read.php

// html部分にデータを追加
<tbody>
  <!-- 🔽 に<tr><td>deadline</td><td>todo</td><tr>の形でデータが入る -->
  <?= $output ?>
</tbody>

```

### 【参考】JS を用いたタグ生成

上記では「PHP 内でタグを生成 → HTML 内に埋め込み」という実装を行っているが，タグ生成部分を JS で行うこともできる．

どちらが正解というものではないので，自身のイメージしやすいパターンで実装すれば問題ない．

```php
<?php

// DB接続，SQL実行など

if ($status == false) {
  $error = $stmt->errorInfo();
  exit('sqlError:'.$error[2]);
} else {
  // PHPではデータを取得するところまで実施
  $result = $stmt->fetchAll(PDO::FETCH_ASSOC);
}

?>

<!DOCTYPE html>
  <head>
    // 省略
  </head>
  <body>
    <table>
      <tbody id="output"></tbody>
    <table>

    <script>
      // PHPのデータをJSに渡す
      const resultArray = <?=json_encode($result) ?>;
      // 配列からタグ生成し，#outputに表示する
    </script>
  </body>
</html>


```

## 練習

DB のデータを読み出して表示する処理を実装しよう！

`todo_read.php`で

- DB に接続
- SQL 文を書いて実行
- 取得したデータを HTML に埋め込み

テーブルのデータが画面に一覧で表示されれば OK！

できた人は SQL 文を編集してフィルタリングやソートなどを実装してみよう．
