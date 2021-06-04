# PHPとDBの連携3（編集画面の作成）


## 処理の流れ

更新処理の流れ（登録処理と似ています！）
① 一覧画面に更新ページへのリンクを作成
urlにidを追加： todo_edit.php?id=**
② 更新ページの作成（todo_edit.php）
③ 更新処理の作成（todo_update.php）
④ 一覧画面に戻る

### 一覧画面にリンク追加

```php
foreach ($result as $record) {
  $output .= "
    <tr>
      <td>{$record["deadline"]}</td>
      <td>{$record["todo"]}</td>
      <td>
        <a href='todo_edit.php?id={$record["id"]}'>edit</a>
      </td>
      <td>
        <a href='todo_delete.php?id={$record["id"]}'>delete</a>
      </td>
    </tr>
  ";
}

```

![一覧画面リンク表示](./img/php03_crud02_todo_read.png)

### 編集画面の作成

```php
// 関数ファイル読み込み
include("functions.php");

// 送信されたidをgetで受け取る
$id = $_GET['id'];

// DB接続&id名でテーブルから検索
$pdo = connect_to_db();
$sql = 'SELECT * FROM todo_table WHERE id=:id';
$stmt = $pdo->prepare($sql);
$stmt->bindValue(':id', $id, PDO::PARAM_INT);
$status = $stmt->execute();

// fetch()で1レコード取得できる．
if ($status == false) {
  $error = $stmt->errorInfo();
  echo json_encode(["error_msg" => "{$error[2]}"]);
  exit();
} else {
  $record = $stmt->fetch(PDO::FETCH_ASSOC);
}
?>

// 以下HTML部分
<form action="todo_update.php" method="POST">
  <fieldset>
    <legend>DB連携型todoリスト（編集画面）</legend>
    <a href="todo_read.php">一覧画面</a>
    <div>
      todo: <input type="text" name="todo" value="<?= $record['todo'] ?>">
    </div>
    <div>
      deadline: <input type="date" name="deadline" value="<?= $record['deadline'] ?>">
    </div>
    <div>
      <input type="hidden" name="id" value="<?= $record['id'] ?>">
    </div>
    <div>
      <button>submit</button>
    </div>
  </fieldset>
</form>

```

![編集画面データ表示](./img/php03_crud02_todo_edit.png)


## 練習

以下の処理を実装！
一覧画面にtodo_edit.phpへのリンクを追加！（todo_delete.phpも一緒に！）
todo_edit.phpではデータをIDで検索し，該当するデータを表示！
