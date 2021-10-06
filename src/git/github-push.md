# GitHub に最新版を push

## この手順を行うタイミング

- すでに GitHub リポジトリに登録してあるプロダクトに機能追加，更新などしたとき．

## 【超重要】ディレクトリを変更する

> 💻 ターミナルの操作

- これを忘れると別のファイルを登録することになりものすごく面倒なので注意すること！！
- ターミナルで下記コマンドを入力する．`cd`のあとには必ずスペース入れる．(enter は押さないこと)

```bash
$ cd
```

入力したらプロダクトのフォルダをドラッグ&ドロップする．

すると，「`cd`」の後にパスが表示されるので，間違いなければ「`enter`」を押す．

以降は上記「`add`」「`commit`」「`push`」の流れ．

## ファイルを add

> 💻 ターミナルの操作

```bash
$ git add .
```

## ファイルを commit

> 💻 ターミナルの操作

```bash
$ git commit -m"コミットメッセージ"
```

## ファイルを push

> 💻 ターミナルの操作

```bash
$ git push origin main
```

実行結果

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

ブラウザで GitHub のリポジトリを確認してコードが最新に更新されていれば OK！
