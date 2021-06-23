# GitHubとの接続設定

## GitHubの接続情報を登録

>💻 ターミナルの操作

「GitHubのユーザ名」と「GitHubで使用しているメールアドレス」をローカルPCに登録する．

ターミナルで下記コマンドを入力し，エンターを押す．

**！！！それぞれ自身のアカウントのものを入力すること！！！**

- 1行目はユーザ名を入力する．
- 2行目はメールアドレスを入力する．

```bash
$ git config --global user.name "hoge"
$ git config --global user.email "hoge@example.com"
```


## 内容確認

>💻 ターミナルの操作

以下のコマンドを入力して内容を確認する．

```bash
$ git config -l
```

実行結果（下記以外にいくつか表示される場合もある．下記の内容が含まれていればOK）

```bash
user.name=hoge
user.email=hoge@example.com
```

上で入力した内容に間違いなければOK．


## 接続テスト

>💻 ターミナルの操作

ターミナルで書きを実行．途中でなにか訊かれたら「`yes`」を入力して進める．

```bash
$ ssh -i ~/.ssh/github_rsa git@github.com
```

実行結果（`Hi`の後は自分のユーザ名が表示される）

```bash
Hi hoge! You've successfully authenticated, but GitHub does not provide shell access.
Connection to github.com closed.
```

上記のように表示されれば OK．


## デフォルトブランチの変更

>💻 ターミナルの操作

Gitでソースコードを管理する際には「ブランチ」という考え方が存在する．

GitHubではデフォルトのブランチが`main`という名前になっているが，ローカルのPCでは`master`となっている場合がある（バージョンなどで異なる）．

`main`に統一しておかないと後々面倒なので，下記のコマンドでローカルPCのデフォルトブランチを`main`に変更する．

```bash
$ git config --global init.defaultBranch main
```

