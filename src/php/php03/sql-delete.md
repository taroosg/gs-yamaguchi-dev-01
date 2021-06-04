# PHPとDBの連携5（データ削除処理）

## 削除の処理

```sql
-- DELETE文の基本構造
DELETE FROM テーブル名;

-- 例

-- 全消去
DELETE FROM todo_table;
-- 指定データのみ
DELETE FROM todo_table WHERE id = 2;

-- WHEREで指定しないとテーブルのデータが全滅する！！
-- DELETEすると復旧できないので注意！！

```

## 処理の流れ

削除処理の流れ
済① 一覧画面に削除ページへのリンクを作成
urlにidを追加todo_delete.php?id=**
② 削除処理の作成（todo_delete.php）
③ 一覧画面に戻る



## 削除の実装

```php
$id = $_GET['id'];

include('functions.php');
$pdo = connect_to_db();

// $sql = 'DELETE FROM todo_table WHERE id=:id';
$sql = 'UPDATE todo_table SET is_deleted=1 WHERE id=:id';

$stmt = $pdo->prepare($sql);
$stmt->bindValue(':id', $id, PDO::PARAM_STR);
$status = $stmt->execute();

if ($status == false) {
  $error = $stmt->errorInfo();
  echo json_encode(["error_msg" => "{$error[2]}"]);
  exit();
} else {
  header("Location:todo_read.php");
  exit();
}

```

## 練習

以下の処理を実装！
【済】一覧画面にtodo_delete.phpへのリンクを追加！
todo_delete.phpではデータをIDで検索し，該当するデータを削除！
完了したらtodo_read.phpへ戻る．
削除処理実行後，一覧ページでデータが削除されていればOK！
（phpmyadminでも確認しよう）
