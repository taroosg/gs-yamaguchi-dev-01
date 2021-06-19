# ファイルアップロード実装

## フォームからファイルを送信

ファイルをサーバに送信する場合もこれまで同様フォームから操作するが，一部追記が必要となる．

-  `<input type="file">`を使用．
- 使用時には`<form>`内に「`enctype="multipart/form-data"`」が必須！！
- methodは`POST`を使用！

>【解説 / `enctype="multipart/form-data"`について】
>
> - これまで`<form>`から送信していたのはテキストデータのみであったが，画像や音声のファイルはバイナリ形式である．
>- この2つのデータを混在させてデータを送信する場合にはこの記述が必要となる．

```html
<!-- file_upform.php -->
<form action="file_upload.php" method="POST" enctype="multipart/form-data">
  <!-- 省略 -->
  <input type="file" name="upfile" accept="image/*" capture="camera">
  <!-- 省略 -->
</form>
```

## サーバ側でのファイル保存の流れ

今回は画像ファイルをサーバに送信して保存する処理を実装する．以下の流れで順番に進める．

0. 準備：送信時にエラー等ないかどうか確認する．
1. 送られてきたファイルの情報を取得する（ファイルは自動的にtmp領域に保管されている状態）．
2. ファイル名を準備する（他のファイルと被らないようにするため）．
3. サーバの保存領域に移動（今回は「`upload`」ディレクトリ）．
4. サンプルファイルでは保存した画像ファイルをimgタグで画面に表示する．

### 💡 Key Point

>if文が多いのでコードをどこに書くか確認しましょう！

### 送信時のエラー確認

まず，「送信されたデータを正しく受け取ることができているかどうか」を確認する．

- 「ファイルが送信されていない」 or 「送信時にエラーが発生した」状態はエラーを出して終了させる．
- 送信されたファイルは`$_FILES`で受け取ることができる！
- まずは`var_dump()`でデータを確認すること！

>【参考 / `$_FILES`の中身】
>
>- `$_FILES`には名前，種類，サイズなどファイルに関する情報が含まれている．
>- また，送信時のエラー状況も含まれており，`["error"]`が0の場合は正常に送信されていることを示している．
>
>```bash
>array(1) {
>  ["upfile"] =>
>  array(5) {
>    ["name"] => string(19) "EH91HetUUAgJkWW.jpg"
>    ["type"] => string(10) "image/jpeg"
>    ["tmp_name"] => string(25) "/opt/lampp/temp/phpFq7XJl"
>    ["error"] => int(0)
>    ["size"] => int(85162)
>  }
>}
>
>```


```php
// file_upload.php

if (isset($_FILES['upfile']) && $_FILES['upfile']['error'] == 0) {
  // 送信が正常に行われたときの処理
  // ...
} else {
  exit('Error:画像が送信されていません');
}

```

### 送信されたデータから必要な情報を取得

正しくデータが送信されていれば，ファイル自体はtmp領域に保存された状態になっている．

ここでは，ファイルを指定の場所に保存するために必要な情報を取得する．

必要な情報は以下のとおり．
- ファイル名
- 一時保存されている場所
- 指定の保存場所（前項で作成した`upload`フォルダ）

```php
// file_upload.php

$uploaded_file_name = $_FILES['upfile']['name'];
$temp_path  = $_FILES['upfile']['tmp_name'];
$directory_path = 'upload/';

```

### ファイル名の準備

サーバにファイルを保存する場合は名前の付け方が重要となる．

Webアプリケーションでは様々なユーザが使用することが想定され，ファイル名が重複すると予期せぬ結果が発生するリスクがある．

そのため，ファイルを指定の場所に保存するタイミングで重複しない名前をつけておくことが重要となる．ここでは次の手順で重複しない名前を準備する．

- ファイルの拡張子の種類を取得する．
- ファイルごとにユニークな名前を作成し，末尾に拡張子を追加する．
- 指定の保存場所を追加し，保存用のパスを作成（`upload/hogehoge.png`のような形になる）．

```php
// file_upload.php

$extension = pathinfo($uploaded_file_name, PATHINFO_EXTENSION);
$unique_name = date('YmdHis').md5(session_id()) . '.' . $extension;
$save_path = $directory_path . $unique_name;

```

### 指定の場所に指定の名前でファイルを保存する

ファイル名の準備ができたら，tmp領域から指定の保存場所へファイルを移動する．

移動する際には下記の条件分岐を行う．

- tmp領域にファイルが存在しているかどうか．
- 指定のパスでファイルの保存が成功したかどうか．

双方の条件をクリアした場合は，PHPがファイルを操作するために権限を変更し，画像をHTMLに埋め込む．

HTML内の適当な場所への`$img`の出力を忘れずに！

[権限の参考：https://www.atmarkit.co.jp/ait/articles/1605/23/news020.html](https://www.atmarkit.co.jp/ait/articles/1605/23/news020.html)

[chmodについて：https://www.php.net/manual/ja/function.chmod.php](https://www.php.net/manual/ja/function.chmod.php)

```php
// file_upload.php

if (is_uploaded_file($temp_path)) {
  if (move_uploaded_file($temp_path, $save_path)) {
    chmod($save_path, 0644);
    $img = '<img src="'. $save_path . '" >';
  } else {
    exit('Error:アップロードできませんでした');
  }
} else {
  exit('Error:画像がありません');
}

```


## 練習

ファイルをアップロードする処理を実装しよう．

- `file_upform.php`にアップロード用のフォームを準備しよう！
- `file_upload.php`にアップロード処理を記述して画像をアップロードしよう！

送信側ファイルからファイルをアップロードし，下記の状態になっていればOK！

- 送信したファイルが`upload`フォルダに保存されている．
- 画面に送信したファイルが表示されている．

