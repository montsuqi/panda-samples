# BLOBのアップロードとダウンロードを試すプログラム

初期表示で cobol/demo.png をBLOBIMPORTして画面に表示する。
その後は画面からアップロードされたファイルをcobol/uploaded.pngにBLOBEXPORTする(ファイルに書き出す)。

DBのmonblobテーブルにBLOBIMPORT、BLOBEXPORTされたファイルが格納されている。

* BLOBIMPORT
    * ファイルをmonblobテーブルに登録する
* BLOBEXPORT
    * monblobテーブルのレコードをファイルへ書き出す

## 準備

```
日レセ停止
$ sudo service jma-receipt stop

ビルド
$ make

PostgreSQLユーザ作成(ident認証するためログインユーザと同名)
$ sudo -u postgres createuser -d $USER

DB作成(panda用スキーマ設定がされたDBがある場合は以降スキップ可能)
$ createdb pandatest

panda用スキーマ設定
$ /usr/lib/panda/bin/monsetup -dir directory

## サーバ起動

$ ./init start
```

## クライアント起動

```
$ glclient2
```

サーバ: http://localhost:8000/rpc/
ユーザ: sample
パスワード: sample
SSL設定: なし

## サーバ終了

```
$ ./init stop
$ ./init clean
$ make clean
```
