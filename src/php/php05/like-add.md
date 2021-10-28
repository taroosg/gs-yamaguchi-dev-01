# Like 機能の実装 1（データの追加 1）

前回までに作成した todo リストに Like 機能（Many to Many の関係）を追加する！

## アプリケーションの動作

- 各ユーザは複数の todo に Like し，各 todo は複数のユーザから Like される．
- 一覧画面の Like ボタンをクリックしたら Like することができ，Like 数が一覧画面に表示される．
- Like は 1 ユーザ 1Like に制限する（自演禁止）．

## 必要な作業・処理

- ユーザテーブルといいねテーブルを作成．
- Like ボタン追加．
- Like ボタンクリック時に Like データを作成．
- Like 数を一覧画面に表示する．

## Like テーブルを作成

新しくテーブルを作成する．テーブル名は「`like_table`」とする．

このテーブルでは「どのユーザが」「どの todo に」Like したのかを記録する役割を持つ．

前項の「中間テーブル」にあたる．

### カラム構造

| カラム名     | データ型 | 長さ | その他設定項目                                            |
| ------------ | -------- | ---- | --------------------------------------------------------- |
| `id`         | INT      | 12   | インデックスを「PRIMARY」に設定．</br>「A_I」にチェック． |
| `user_id`    | INT      | 12   |                                                           |
| `todo_id`    | INT      | 12   |                                                           |
| `created_at` | DATETIME | -    |                                                           |

## todo リストの Like 機能実装

### やりたいこと

いいねボタンをクリックしたら．．．

- like_table に「誰が」「何に」いいねをしたのかを追加

実装の方針

- todo_read.php にいいねボタンを設置
- GET で todo の id とユーザの id を送信する
- 受け取り側のファイル（like_create.php）で受け取ったデータを db に登録

## todo 一覧画面に Like ボタンの設置

一覧画面のタグ生成部分に Like ボタンを追記する．

user_id はログイン時にセッション変数に保存している値を使用する（`todo_login_act.php`に追記）．

```php
// todo_login_act.php

if (!$val) {
  echo "<p>ログイン情報に誤りがあります</p>";
  echo "<a href=todo_login.php>ログイン</a>";
  exit();
} else {
  $_SESSION = array();
  // 🔽 ここを追記
  $_SESSION['user_id'] = $val['id'];
  $_SESSION['session_id'] = session_id();
  $_SESSION['is_admin'] = $val['is_admin'];
  $_SESSION['username'] = $val['username'];
  header("Location:todo_read.php");
  exit();
}

```

`user_id`と`todo_id`を`like_create.php`に GET で送信する．

```php
// todo_read.php

$user_id = $_SESSION['user_id'];

// 🔽 タグ生成部分
foreach ($result as $record) {
  $output .= "
    <tr>
      <td>{$record["deadline"]}</td>
      <td>{$record["todo"]}</td>
      // 🔽 ここ1行追記
      <td><a href='like_create.php?user_id={$user_id}&todo_id={$record["id"]}'>like</a></td>
      <td><a href='todo_edit.php?id={$record["id"]}'>edit</a></td>
      <td><a href='todo_delete.php?id={$record["id"]}'>delete</a></td>
    </tr>
  ";
}

```

## Like データの追加

Like テーブルに GET で送信されてきた内容を追加する．

処理の流れ自体はシンプルな INSERT 処理．

```php
// like_create.php

include('functions.php');

$user_id = $_GET['user_id'];
$todo_id = $_GET['todo_id'];

$pdo = connect_to_db();

$sql = 'INSERT INTO like_table (id, user_id, todo_id, created_at) VALUES (NULL, :user_id, :todo_id, now())';

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

## 練習

todo リストに Like 機能を追加しよう．

- `todo_read.php`に Like ボタンを追加．
- `like_create.php`でテーブルにデータ作成．

Like ボタンをクリックして，Like テーブルにデータが作成されていれば OK．

（phpmyadmin でデータを確認しよう）
