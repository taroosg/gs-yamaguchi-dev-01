# ファイルアップロードと DB 連携

ファイルをサーバの指定した場所に保存することはできたが，このままでは使い勝手が良くない．

ファイルの保存場所を記録しておくことで，他のデータを連携させてアプリケーション上で扱えるようになる．

今回は DB と連携させて，前回までに実装した todo リストに組み込む．流れは先程までとほぼ同様だ．

## やることの流れ

### 送信側

- todo などのデータを一緒に画像ファイルを送信する．

### 受信側

0. 準備：送信時にエラー等ないかどうか確認する．
1. 送られてきたファイルの情報を取得する（ファイルは自動的に tmp 領域に保管されている状態）．
2. ファイル名を準備する（他のファイルと被らないようにするため）．
3. サーバの保存領域に移動（今回は「`upload`」ディレクトリ）．
4. todo などのデータを一緒に，「保存場所のパス」をテーブルに保存する．

## 準備

「ファイルの保存場所のパス」をテーブルに記録したいので，カラムを追加する．

phpmyadmin から，これまで使用していた`todo_table`に`image`カラムを追加しよう．

| カラム名     | データ型 | 長さ | その他設定項目                                            |
| ------------ | -------- | ---- | --------------------------------------------------------- |
| `id`         | INT      | 12   | インデックスを「PRIMARY」に設定．</br>「A_I」にチェック． |
| `todo`       | VARCHAR  | 128  |                                                           |
| `deadline`   | DATE     | -    |                                                           |
| `image`      | VARCHAR  | 128  | 「`Null`にチェックを入れる．」                            |
| `created_at` | DATETIME | -    |                                                           |
| `updated_at` | DATETIME | -    |                                                           |

## 送信側の処理

送信側のフォームでは以下の点を追記しよう．

- ファイル送信用に`<input type="file">`を追加．
- `action`をファイル保存用の`create_file.php`に変更．
- `enctype`属性の追加．

```html
<!-- todo_input.php -->

<form action="create_file.php" method="post" enctype="multipart/form-data">
  <!-- 省略 -->
  <div>
    <input type="file" name="upfile" accept="image/*" capture="camera" />
  </div>
  <!-- 省略 -->
</form>
```

## 受信側の処理

こちらも前項の内容とほぼ同じであるが，ファイルの保存後が異なる．

0. 準備：送信時にエラー等ないかどうか確認する．
1. 送られてきたファイルの情報を取得する．
2. ファイル名を準備する．
3. サーバの保存領域に移動（前項と同じ「`upload`」ディレクトリ）．

-- ここまで前項の処理と全く同じ --

4. 「POST で受け取った todo のデータ」と「ファイルを保存したパス」をテーブルに保存する．
5. 一覧画面に画像が表示されるよう追記．

### ファイル保存の処理

前項までと全く同様のコード．ただし，今回は画像を表示する必要がないため，権限の変更までの処理で十分である．

```php
// create_file.php

// 他ファイル読み込み，POSTデータの受け取りなど

// データの確認
if (isset($_FILES['upfile']) && $_FILES['upfile']['error'] == 0) {
  // 情報の取得
  $uploaded_file_name = $_FILES['upfile']['name'];
  $temp_path  = $_FILES['upfile']['tmp_name'];
  $directory_path = 'upload/';
  // ファイル名の準備
  $extension = pathinfo($uploaded_file_name, PATHINFO_EXTENSION);
  $unique_name = date('YmdHis').md5(session_id()) . '.' . $extension;
  $save_path = $directory_path . $unique_name;
  // 今回は画面に表示しないので権限の変更までで終了
  if (is_uploaded_file($temp_path)) {
    if (move_uploaded_file($temp_path, $save_path)) {
      chmod($save_path, 0644);
    } else {
      exit('Error:アップロードできませんでした');
    }
  } else {
    exit('Error:画像がありません');
  }
} else {
  exit('Error:画像が送信されていません');
}

```

### DB への情報追加

ここまでで指定の場所にファイルを保存できたので，次は保存したパスをテーブルに追加する．

流れはいつもどおり「DB 接続」 -> 「SQL 文作成&実行」．

`image`カラムを追加しているため，「カラム名」「バインド変数」を追加する．ファイル保存の際に使用した`$save_path`を`image`カラムに入れるよう設定している．

```php
// create_file.php

// ファイル保存処理など

$pdo = connect_to_db();

$sql = 'INSERT INTO todo_table(id, todo, deadline, image, created_at, updated_at) VALUES(NULL, :todo, :deadline, :image, sysdate(), sysdate())';

$stmt = $pdo->prepare($sql);
$stmt->bindValue(':todo', $todo, PDO::PARAM_STR);
$stmt->bindValue(':deadline', $deadline, PDO::PARAM_STR);
$stmt->bindValue(':image', $save_path, PDO::PARAM_STR);

try {
  $status = $stmt->execute();
} catch (PDOException $e) {
  echo json_encode(["sql error" => "{$e->getMessage()}"]);
  exit();
}

header("Location:todo_input.php");
exit();

```

### 一覧画面での画像表示

テーブルに画像パスを保存できたら，後は呼び出して`<img>`の中に`image`カラムの値を設定すれば該当する画像が表示される．

delete ボタンの後あたりに表示させてみると良いだろう．

```php
// todo_read.php

// 省略

// タグ生成部分
foreach ($result as $record) {
  $output .= "
    <tr>
      <td>{$record["deadline"]}</td>
      <td>{$record["todo"]}</td>
      <td><a href='like_create.php?user_id={$user_id}&todo_id={$record["id"]}'>like{$record["like_count"]}</a></td>
      <td><a href='todo_edit.php?id={$record["id"]}'>edit</a></td>
      <td><a href='todo_delete.php?id={$record["id"]}'>delete</a></td>
      <td><img src='{$record["image"]}' height='150px'></td>
    </tr>
  ";
}

// 省略

```

## 練習

ファイルをアップロードする処理を実装しよう．

- `todo_input.php`にアップロード用のフォームを準備しよう！
- `create_file.php`にアップロード処理を記述して画像をアップロードし，DB と連携させよう！
- `todo_read.php`に画像を表示させよう！

送信側ファイル（`todo_input.php`）からファイルをアップロードし，下記の状態になっていれば OK！

- 送信したファイルが`upload`フォルダに保存されている．
- 画像の保存パスが`todo_table`の`image`カラムに保存されている．
- 一覧画面（`todo_read.php`）に画像が表示されている．

アップロード用のフォームを準備しよう！（todo_input.php）
アップロード処理を記述して画像をアップロードしよう！（create_file.php）
アップロードしたファイルの URL を DB に保存しよう！（create_file.php）
一覧画面に画像を表示しよう！（todo_read.php）
-> 「画像が`upload`フォルダに保存」されて「パスが DB に保存」されていれば OK！
-> 一覧画面で画像が表示されれば OK！

> 【参考 / ファイル送信を任意にする】
>
> - 現在の状況では，ファイル送信が必須になっている．
> - ファイルを「送信してもしなくても良い」ようにするには条件分岐を工夫してやれば良い．
> - 未送信時には`$_FILES`内の`['error']`が`4`であることを利用して条件を分ける．
>
> ```php
> // create_file.php
>
> if ($_FILES['upfile']['error'] == 4) {
>  $save_path = null;
> } else if ($_FILES['upfile']['error'] == 0) {
>  // ファイルを保存する処理
> } else {
>  exit('アップロードに失敗しました');
> }
>
> ```
