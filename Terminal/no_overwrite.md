# リダイレクトで .bashrc を吹き飛ばさないために上書きを禁じる

`echo "追記したかったエイリアス" > ~/.bashrc` で共有 PC の .bashrc を吹き飛ばしてしまった．ごめんなさい．復旧は多分できたのと再発を防げるよう設定したので許してほしいです．

## リダイレクト

コマンドの出力を指定したファイルに移す．虚無に捨てることもできる．

`>` を使うと新規作成，`>>` を使うと追記．本事件は `>>` を使うべきところで `>` を打ってしまったがゆえに起きた．

## シェル設定

```sh
$ set -o | grep noclobber
noclobber             off
```

.bashrc に `set -o noclobber` と書くと `>` では存在するファイルを上書きできなくなる．`>|` を使うと上書き可能．

```sh
$ set -o | grep noclobber
noclobber             on
$ set -o | grep noclobber > a.txt  # これはうまくいく
$ set -o | grep noaliases > a.txt
zsh: file exists: a.txt
$ set -o | grep noaliases >| a.txt  # これもうまくいく
```
