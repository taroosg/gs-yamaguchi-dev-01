# Like 機能の実装 2（データの追加 2）

## ここまでの Like 機能の問題点

### 現状

- 連打すれば無限に Like できてしまう．．．
- Like している状況であれば，Like を取り消す処理にしたい！

### 実装の方針

- Like ボタンをクリックしたら，まず todo と user でテーブルを検索する．
- データが 1 件以上存在すれば DELETE の SQL を実行する．
- データが存在しなければ INSERT の SQL（前項で実装したもの）を実行する．

## Like 状態の調査

前項で作成した`like_create.php`の INSERT 処理の前にデータの件数を確認したい．

件数の確認には`COUNT()`関数を使用する．

```php
// like_create.php

// 省略

$sql = 'SELECT COUNT(*) FROM like_table WHERE user_id=:user_id AND todo_id=:todo_id';
$stmt = $pdo->prepare($sql);
$stmt->bindValue(':user_id', $user_id, PDO::PARAM_STR);
$stmt->bindValue(':todo_id', $todo_id, PDO::PARAM_STR);

try {
  $status = $stmt->execute();
} catch (PDOException $e) {
  echo json_encode(["sql error" => "{$e->getMessage()}"]);
  exit();
}

$like_count = $stmt->fetchColumn();
// まずはデータ確認
var_dump($like_count);
exit();

```

## Like 数で条件分岐（削除 or 作成）

`$like_count`で条件に該当するデータの件数が取得できるのでまずは確認する．

データの件数が確認できたら，件数が 0 かそれ以外で条件分岐する．0 件でなければ DELETE 文が作成され，0 件の場合は INSERT 文が作成される．

```php
// like_create.php

if ($like_count != 0) {
  // いいねされている状態
  $sql = 'DELETE FROM like_table WHERE user_id=:user_id AND todo_id=:todo_id';
} else {
  // いいねされていない状態
  $sql = 'INSERT INTO like_table (id, user_id, todo_id, created_at) VALUES (NULL, :user_id, :todo_id, sysdate())';
}

// 以下は前項と変更なし
$stmt = $pdo->prepare($sql);
$stmt->bindValue(':user_id', $user_id, PDO::PARAM_STR);
$stmt->bindValue(':todo_id', $todo_id, PDO::PARAM_STR);

try {
  $status = $stmt->execute();
} catch (PDOException $e) {
  echo json_encode(["sql error" => "{$e->getMessage()}"]);
  exit();
}

header("Location:todo_read.php");
exit();

```

このように記述することで，1 ユーザ 1Like の状態を実現することができる．

## 練習

todo リストの Like 機能を編集しよう．

- `like_create.php`で Like 数カウント -> 条件分岐して DELETE or INSERT．

以下 2 条件で動作確認！

- 「Like されていない状態」で Like ボタンをクリックして，Like テーブルにデータが作成されていれば OK．
- 「Like されている状態」で Like ボタンをクリックして，Like テーブルのデータが削除されていれば OK．

phpmyadmin でデータを確認し，10 件程度データが入っている状態にしておこう．
