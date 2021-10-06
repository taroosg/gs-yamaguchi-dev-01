# SSH 鍵の発行

## 作業ディレクトリの確認

> 💻 ターミナルの操作

ターミナルを起動するとホームディレクトリにいるはずだが一応下記を実行．

```bash
$ cd ~
```

## フォルダの準備

> 💻 ターミナルの操作

- ssh-key は適切な場所に配置しないと動かない．
- 以下の手順でフォルダを準備する．

下記コマンドでファイルとフォルダの一覧を表示する．

```bash
$ ls -a
```

一覧が表示されるので，「`.ssh`」フォルダを探す．

**`「.ssh」`が存在しない場合のみ**下記コマンドでホームディレクトリに`.ssh`フォルダを作成する．

```bash
$ mkdir -p ~/.ssh
```

エラーが出なければ OK．

## ssh-key の発行

> 💻 ターミナルの操作

- GitHub にアクセスするには ssh-key が必要となる．
- ssh-key は公開鍵と秘密鍵のペアになっており，「公開鍵を GitHub に登録」「秘密鍵を PC のローカルに保存」することで通信時に組み合わせがあっているかどうか判断する．
- ターミナル(windows は GitBash)を開いて以下のコマンドを入力する．

まずは以下のコマンドで作業ディレクトリを`.ssh`（前項で準備したフォルダ）に変更する．

```bash
$ cd ~/.ssh
```

続いて，以下のコマンドで ssh キー（公開鍵と秘密鍵のペア）を発行する．

```bash
$ ssh-keygen
```

実行結果

```bash
Generating public/private rsa key pair.
Enter file in which to save the key (/home/vagrant/.ssh/id_rsa):
```

そのまま何も入力せずに Enter．

```bash
Enter passphrase (empty for no passphrase):
```

続き．何も入力せずに Enter．

```bash
Enter same passphrase again:
```

続き．パスワード入力していないので何も入力せずに Enter．

```bash
Your identification has been saved in id_rsa.
Your public key has been saved in id_rsa.pub.
The key fingerprint is:
6f:09:00:22:44:55:66:77:95:89:41:7d:a7:58:1b:92 vagrant@localhost.localdomain
The key's randomart image is:
+--[ RSA 2048]----+
|   .o. .         |
|     oEo+ .      |
|    . +=+=       |
|     o.+==       |
|    . . S .      |
|       - + .     |
|      .   +      |
|         .       |
|                 |
+-----------------+
```

これで ssh-key を発行できた．

> **【参考】**
>
> 以下のコマンドで発行した内容を確認できるので，うまくいかない場合は確認してみると良い．
>
> 下記のようになっていれば OK．（細かな文字列や数値は異なっていて OK）．
>
> ```bash
> $ ls -la | grep id_rsa
>
> # 実行結果
> -rw-------  1 taroosg taroosg 1856 Dec 28  2018 id_rsa
> -rw-rw-r--  1 taroosg taroosg  403 Dec 28  2018 id_rsa.pub
> ```

## ssh キーの設定

> 💻 ターミナルの操作

以下 2 つのコマンドで ssh-key を動作するように設定する．

```bash
$ eval $(ssh-agent)

# 実行結果（数値は毎回異なる）
Agent pid 9899

```

```bash
$ ssh-add ~/.ssh/id_rsa

# 実行結果（ディレクトリは各自異なる）
Identity added: /home/taroosg/.ssh/id_rsa

```

以上で ssh-key の準備は完了だが，設定ファイルに変更を加える必要がある．
