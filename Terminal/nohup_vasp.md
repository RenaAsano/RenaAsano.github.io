# SSH を利用して一歩も動かず VASP 計算

VASP 計算のために共用 PC の前に行くのが面倒な人向け

## SSH 設定

自身の PC から VASP が入ってる PC に SSH 接続できればいいです．

## エイリアス設定

```sh
alias vasp_std='path/to/your/vasp/bin/vasp_std'
alias nohup='nohup '
```

VASP 実行ファイルへのパスは普通に通していいと思うけど，うちはなぜかエイリアスになってました．

## 実際の操作

### SSH 接続

```sh
ssh your_vasp_pc
cd your_work_dir
```

~/.ssh/config で色々設定してある前提の接続方法です．

### VASP 実行

```sh
nohup vasp_std > out.log &
```

標準出力を out.log へリダイレクトして記録します．このコマンドは `ctrl + C` で中断されません．

### 出力の監視

```sh
tail -f out.log
```

リアルタイムに出力を見られます．他のことをしたくなったら `ctrl + C` で中断．

### 実行状況の確認

#### `jobs` で確認

```sh
jobs
```

ディレクトリの表示もしてくれて嬉しい．

#### `ps` で確認

```sh
ps ux | grep vasp
```

`ps ux` コマンドで今実行されている処理の一覧を得て，その中から vasp_* コマンドの情報を掴み取ります．

### 計算の中断

#### `jobs` と `fg` で中断

```sh
$ jobs
[1]
$ fg 1
```

この後 `ctrl + C` で中断

#### `ps` と `kill` で中断

```sh
ps ux | grep vasp
```

開始時刻やユーザーで特定して出力の左から 2 番目の数字 (プロセス ID) を使用

```sh
kill -9 your_PID
```
