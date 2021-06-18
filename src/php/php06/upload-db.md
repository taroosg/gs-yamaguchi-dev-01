# ファイルアップロードとDB連携

1. フォーム（`<form>`）からアップロードする．
2. tmp領域（一時保存場所）に自動的に保存される．
3. サーバの保存領域に移動（今回は「`upload`」ディレクトリとする）
データベースに保存場所のパスを登録

準備①
todo_tableにカラムを追加する．
「image」を追加！
保存した画像のURLを登録する．

|カラム名|データ型|長さ|その他設定項目|
|---|---|---|---|
|`id`|INT|12|インデックスを「PRIMARY」に設定．</br>「A_I」にチェック．|
|`todo`|VARCHAR|128||
|`deadline`|DATE|-||
|`image`|VARCHAR|128||
|`created_at`|DATETIME|-||
|`updated_at`|DATETIME|-||

form追加する
```html
// input type="file"の追加，actionの宛先変更，enctype属性の追加
// （流れはさっきやったものと同じ）

<form method="post" action="create_file.php" enctype="multipart/form-data">
  // …
  <div>
    <input type="file" name="upfile"
           accept="image/*"capture="camera">
  </div>
  // ...
</form>
```

準備：送信時にエラー等ないかどうか確認．
送られてきたファイルの情報を取得（自動的にtmp領域に保管）
ファイル名を準備（他のファイルと被らないように）
サーバの保存領域に移動（サンプルでは「upload」）
（ファイル名に保存ディレクトリも含めている点に注意！）
-- ここまで前項の処理と全く同じ --
DBに情報を作成
一覧画面に画像を表示

コードはさっきのと同じ

```php
```

アップロード領域へファイルを移動．
権限の変更．
今回は表示しない！（imgタグを作成しない）

```php
if (is_uploaded_file($temp_path)) {
  if (move_uploaded_file($temp_path, $filename_to_save)) {
    chmod($filename_to_save, 0644);			// 権限の変更
	// 今回は権限を変更するところまで
  } else {
    exit('Error:アップロードできませんでした');	// 画像の保存に失敗
  }
} else {
  exit('Error:画像がありません');			// tmpフォルダにデータがない
}
```

```php
// 他のデータと一緒にDBへ登録！
// 処理の流れはtodo_create.phpと同様

// INSERT文にimageカラムを追加！
// imageカラムには画像ファイルのパスが入る．
$sql ='INSERT INTO
       todo_table(id, todo, deadline, image, created_at, updated_at)
       VALUES(NULL, :todo, :deadline, :image, sysdate(),sysdate())';
// ...省略（todo_create.phpと同様）
$stmt->bindValue(':image', $filename_to_save, PDO::PARAM_STR);
// ...実行，エラー処理，etc...

```

```php
// 一覧画面で画像を表示


// ...
$output .= "<td><img src='{$record["image"]}' height=150px></td>";
// ...

```

練習
アップロード用のフォームを準備しよう！（todo_input.php）
アップロード処理を記述して画像をアップロードしよう！（create_file.php）
アップロードしたファイルのURLをDBに保存しよう！（create_file.php）
一覧画面に画像を表示しよう！（todo_read.php）
-> 「画像が`upload`フォルダに保存」されて「パスがDBに保存」されていればOK！
-> 一覧画面で画像が表示されればOK！
