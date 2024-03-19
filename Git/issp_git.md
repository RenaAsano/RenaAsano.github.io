# ISSP のデータを GitLab にバックアップ

ISSP のデータを sftp でコピーしては複製を量産したくない人向け

## ディレクトリ構成

全てのデータを Git リポジトリ内に含める

## 注意

どう考えても Private リポジトリにすべき

## 結論

`rsync` コマンドでより安全 (GitLab 不要) に同期させられたのでこの記事の需要は潰えた