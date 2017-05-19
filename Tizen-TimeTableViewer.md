## これは何？
NextTrain 形式データの時刻表表示と、カウントダウンを行なう Tizen wareable 向けアプリです。

## プログラムの元
プログラムのキモというか本体には [Js-TT](http://hazelnutworks.com/cgi-bin/wiki/wiki.cgi?page=Js-TT) を利用させていただいています。  
ソースの再利用の快諾くださった 作者の Hazelnut様には感謝。


## 対象機種
 - Gear S  開発環境のため、動作確認済み。アプリストアに公開

## Install 方法
アプリストアから「時刻表」で検索してダウンロードしてください。

## Uninstall 方法
Gear Manager からアプリケーションのアンインストールを行なってください。

## 使用方法 
アプリをインストールして起動すると Documents/timetable フォルダが作成され、合わせてサンプルのタイムテーブル(sample.tbl)が作成されます。  
サンプルデータが不要になった場合は、ファイルを削除してください。

NextTrain の tbl ファイルを UTF-8 形式で、拡張子を .tbl にして Documents/timetableに置いてください。  
アプリ起動時にフォルダ内の 拡張子が .tbl になっているファイルを読み込みます。

あとは、時刻表選択から任意の時刻表を選べば現在の時刻に合わせて電車の来る時間を表示します。  
使い方は [Js-TT](http://hazelnutworks.com/cgi-bin/wiki/wiki.cgi?page=Js-TT) のページも参考にしてみてください。

## 画面イメージ
![Screenshot1](/images/TimeTable/Screenshot1.png)
![Screenshot2](/images/TimeTable/Screenshot2.png)
![Screenshot3](/images/TimeTable/Screenshot3.png)
![Screenshot4](/images/TimeTable/Screenshot4.png)

## 変更履歴
 - 1.0.0 初版

## ソースコード
https://github.com/tesurijp/TimeTableViewer
