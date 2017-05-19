## これは何？
2段階認証で使われる TOTP キーを表示する Tizen wareable 向けアプリです。


## 対象機種
 - Gear S  開発環境のため、動作確認済み。アプリストアに公開
 - Gear S2  開発環境のため、動作確認済み。アプリストアに公開
 - Gear S3  動くらしいですが持ってないので未確認

## Install 方法
アプリストアから「TOTP」で検索してダウンロードしてください。

## Uninstall 方法
Gear Manager からアプリケーションのアンインストールを行なってください。

## 使用方法 
以下のような形式の auth_keyinfo.txt ファイルをGear端末の Documents フォルダに置いて、アプリを起動してください。  
```
Service1:Account_A:JBSWY3DPEHPK3PXP
Service2:Account@B:JBSWY34PXP
Service3:AccountC:JBSWY3DPEHPK3PXP
```
: (コロン) で区切って、サービス名、アカウント名、シークレットキーの順に並べます。  
サービス名、アカウント名は、表示の区別のためなので、わかりやすい名前でかまいません。  

Gear S に関しては PC と接続して Documents フォルダに置けば完了です。  
~~Gear S2/S3 に関しては PC と接続ができませんので、Filemaster のようなユーティリティアプリを使う必要があります。~~  
Gear S2/S3 バージョンはファイルを転送する2つの場所を追加しました。
 - SDK(sdb) を使って Downloads フォルダにコピー
 - ファイル名を auth_keyinfo.mp3 に変更して、GearManager から音楽データとして Gear端末に転送

## 変更履歴
 - 1.0.0 初版
 - 1.1.0 Gear S2 のみ

## ソースコード
https://github.com/tesurijp/TOTP-Tizen
