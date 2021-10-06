# GitHub にプロダクトを push

## この手順を行うタイミング

- 新しいプロダクトを作成し，初めて GitHub にソースコードを共有するとき．

## リポジトリを作成する

> 🌏 ブラウザの操作

- ブラウザで GitHub にアクセスし，新しいリポジトリを作成する．
- Repository name はプロダクト名にしておくとわかりやすくて良い．(janken, mamopad など)
- 【重要】下の方の`Initialize this repository with:`部分はチェックを入れないこと．
- 作成すると URL が表示されるのでそのままにしておく．「SSH のタブ」を選択しておく(後で URL を使用するため)

## 【超重要】ディレクトリを変更する

> 💻 ターミナルの操作

まず，ターミナルの作業ディレクトリをプロダクトのディレクトリに移動する必要がある．

**移動しない場合，PC の中身全てを GitHub にプッシュする羽目になるので必ず行うこと！！**

**この手順を行わなかった場合，今後あらゆるコマンドでエラーが発生する，PC がクラッシュするなどの危険が伴う．**

ターミナルで下記コマンドを入力する．(enter は押さないこと)

【重要】`cd`のあとにスペースを入れること

```bash
$ cd
```

入力したらプロダクトのフォルダをターミナルのウインドウ内にドラッグ&ドロップする．

すると，「`cd`」の後にパスが表示されるので，間違いなければ「`enter`」を押す．

## 初期化

> 💻 ターミナルの操作

プロダクトのフォルダで Git による管理をできるようにする．

下記コマンドを入力する．

```bash
$ git init
```

## リポジトリの登録

> 💻 ターミナルの操作

コードをアップするリポジトリを連携させる．

先程ブラウザで作成したリポジトリの URL（`git@github.com/***`）を使用する．

ターミナルで以下を実行する．

```bash
$ git remote add origin リポジトリのURL
```

登録されているかどうかは以下のコマンドで確認できる．

```bash
$ git remote -v
```

確認結果

```bash
origin	git@github.com:******/******.git (fetch)
origin	git@github.com:******/******.git (push)
```

間違っている場合は以下で登録し直す．

```bash
$ git remote set-url origin 正しいURL
```

## ファイルを add

> 💻 ターミナルの操作

Git で管理するファイルを指定する．アップするには「`add`」「`commit`」「`push`」の 3 手順が必要．

ターミナルで以下を実行する．`.` は「フォルダ内の全てのファイル」の意味で，`add` の後にはスペースが入る点に注意！

```bash
$ git add .
```

## ファイルを commit

> 💻 ターミナルの操作

`commit` はファイルのバージョンを作成するイメージ．

コミットを重ねても，以前のコミットへ状態を戻すことでファイルの内容をもとに戻すことが可能．

以下のコマンドを入力する．

`-m` のあとの「`""`」内にコミットメッセージを追加する．(変更内容などが把握できるコメント)

```bash
$ git commit -m "コミットメッセージ"
```

## ファイルを push

> 💻 ターミナルの操作

`push` は実際にファイルをアップロードするイメージ．この段階ではじめて GitHub にコードが追加される．

下記コマンドを入力する．

```bash
$ git push origin main
```

実行結果（似たような感じになっていれば OK）

```bash
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 385 bytes | 385.00 KiB/s, done.
Total 4 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
To github.com:******/******.git
   9ae72be..eb700ec  main -> main
```

ブラウザで GitHub のページを確認し，ファイルがアップされていれば成功！
