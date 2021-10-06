# GitHub との接続設定

## GitHub の接続情報を登録

> 💻 ターミナルの操作

「GitHub のユーザ名」と「GitHub で使用しているメールアドレス」をローカル PC に登録する．

ターミナルで下記コマンドを入力し，エンターを押す．

**！！！それぞれ自身のアカウントのものを入力すること！！！**

- 1 行目はユーザ名を入力する．
- 2 行目はメールアドレスを入力する．

```bash
$ git config --global user.name "hoge"
$ git config --global user.email "hoge@example.com"
```

## 内容確認

> 💻 ターミナルの操作

以下のコマンドを入力して内容を確認する．

```bash
$ git config -l

# 実行結果（下記以外にいくつか表示される場合もある．下記の内容が含まれていればOK）
user.name=hoge
user.email=hoge@example.com

```

上で入力した内容に間違いなければ OK．

## 接続テスト

> 💻 ターミナルの操作

ターミナルで下記を実行．途中でなにか訊かれたら「`yes`」と入力して進める．

```bash
$ ssh -i ~/.ssh/id_rsa git@github.com

# 実行結果（`Hi` の後は自分のユーザ名が表示される）
Hi hoge! You've successfully authenticated, but GitHub does not provide shell access.
Connection to github.com closed.
```

上記のように表示されれば OK．

## デフォルトブランチの変更

> 💻 ターミナルの操作

Git でソースコードを管理する際には「ブランチ」という考え方が存在する．

GitHub ではデフォルトのブランチが`main`という名前になっているが，ローカルの PC では`master`となっている場合がある（バージョンなどで異なる）．

`main`に統一しておかないと後々面倒なので，下記のコマンドでローカル PC のデフォルトブランチを`main`に変更する．

```bash
$ git config --global init.defaultBranch main
```
