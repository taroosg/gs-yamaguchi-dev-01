# ファイルの準備と動作確認

## 必要なファイルの準備

1. 新しいフォルダをデスクトップに作成
2. vs code を開き「file」→「open」 -> 上で作成したフォルダを選択
3. 左側の「New File」をクリック -> 「index.html」と入力
4. 左側の「New File」をクリック -> 「css」と入力
5. css フォルダを選択して「New File」をクリック -> 「main.css」
6. サンプルの「img」フォルダを作成したフォルダの中に入れる

↓ このような構成になっていれば OK！

```txt
.
├── css
│   └── main.css
├── img
│   ├── content_img.jpg
│   └── main_bg.jpg
└── index.html

```

## HTML の準備

1. web ページのフォーマットを入力
2. index.html を開く
3. 「!」を入力（必ず半角）
4. 「tab」を押す
5. 下のようになれば OK！

HTML の構造

```html
<!-- index.html -->

<!DOCTYPE html>
<html lang="en">
  <head>
    <!-- 文書自体の情報（文書名・読み込むファイルなど） -->
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
  </head>
  <body>
    <!-- 実際の文章の内容（文章や画像など）．ここにコンテンツを記述する． -->
  </body>
</html>
```

## CSS ファイルの読み込み

html ファイルと css ファイルの関連付け

1. index.html を開く
2. 「`<title>`...」の 1 行下で「link」を入力して tab キー
3. タグができるので，「`href=`」の後を「`css/main.css`」に変更

```html
<!-- index.html -->

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <!-- 🔽 下記 1 行を追加 🔽 -->
    <link rel="stylesheet" href="css/main.css" />
  </head>

  <body></body>
</html>
```

## HTML の動作確認

`<body>` タグ内にタグを作成して動作を確認する．

```html
<!-- index.html -->

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>ここがページのタイトルなので好きな名前に変えても良き</title>
    <link rel="stylesheet" href="css/main.css" />
  </head>
  <body>
    <!-- 🔽 下記 1 行を追加 🔽 -->
    <h1>Hello World!</h1>
  </body>
</html>
```

ブラウザ画面で「Hello World!」が表示されれば OK！

![Hello World 確認]()

> **💡 開発の流れ**
>
> エディタでコードを書く
> 保存する（command + s, ctrl + s）
> vs code でファイル名を右クリック →「Copy Path」
> ブラウザのアドレスバーに貼り付けて Enter
> 意図したとおりになっているかどうか確認（今回は ↓ のようになれば OK）
