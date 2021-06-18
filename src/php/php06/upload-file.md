# ファイルアップロード実装

①フォームからアップロード（file_upform.php）

// <input type="file">を使用．
// 使用時には「enctype="multipart/form-data"」が必須！！
// methodはpostを使用！getだと容量不足の可能性が．．．！

// コード
```html
<form action="file_upload.php"
      method="POST"
      enctype="multipart/form-data">
  // ...
  <input type="file" name="upfile" accept="image/*"capture="camera">
  // ...
</form>
```

ファイル保存の流れ（file_upload.php）

準備：送信時にエラー等ないかどうか確認．
送られてきたファイルの情報を取得（自動的にtmp領域に保管）
ファイル名を準備（他のファイルと被らないように）
サーバの保存領域に移動（サンプルでは「upload」）
（ファイル名に保存ディレクトリも含めている点に注意！）
サンプルファイルではimgタグで表示

if文が多いのでコードをどこに書くか確認しましょう！

```php
// ファイルが追加されていない or エラー発生の場合を分ける．
// 送信されたファイルは$_FILES['...'];で受け取る！

// コード
if (isset($_FILES['upfile']) && $_FILES['upfile']['error'] == 0) {
  // 送信が正常に行われたときの処理（この後記述）
  ...
} else {
  // 送られていない，エラーが発生，などの場合
  exit('Error:画像が送信されていません');
}
```

```php
// アップロードしたファイル名を取得．
// 一時保管しているtmpフォルダの場所の取得．
// アップロード先のパスの設定（サンプルではuploadフォルダ <- 作成！）

// コード
$uploaded_file_name = $_FILES['upfile']['name'];	//ファイル名の取得
$temp_path  = $_FILES['upfile']['tmp_name'];		//tmpフォルダの場所
$directory_path = 'upload/';						//アップロード先ォルダ
													// （↑自分で決める）

```

```php
// ファイルの拡張子の種類を取得．
// ファイルごとにユニークな名前を作成．（最後に拡張子を追加）
// ファイルの保存場所をファイル名に追加．

// コード
$extension = pathinfo($uploaded_file_name, PATHINFO_EXTENSION);
$unique_name = date('YmdHis').md5(session_id()) . "." . $extension;
$filename_to_save = $directory_path . $unique_name;

// 最終的に「upload/hogehoge.png」のような形になる
```

アップロード領域へファイルを移動．
権限の変更．
`<img>`で出力．
    ※権限：https://www.atmarkit.co.jp/ait/articles/1605/23/news020.html

```php
if (is_uploaded_file($temp_path)) {
  // ↓ここでtmpファイルを移動する
  if (move_uploaded_file($temp_path, $filename_to_save)) {
    chmod($filename_to_save, 0644);					// 権限の変更
    $img = '<img src="'. $filename_to_save . '" >';	// imgタグを設定
  } else {
    exit('Error:アップロードできませんでした');	// 画像の保存に失敗
  }
} else {
  exit('Error:画像がありません');			// tmpフォルダにデータがない
}
```

練習
アップロード用のフォームを準備しよう！（file_upform.php）
アップロード処理を記述して画像をアップロードしよう！
アップロードしたファイルを表示しよう！
（file_upload.phpで$imgを出力！）
-> 「画像が`upload`ファルダに保存」されて「画面に表示」されていればOK
