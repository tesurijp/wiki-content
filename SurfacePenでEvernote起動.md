まずは[AutoHotKey](http://www.autohotkey.com/)を用意

SurfacePen3 のトップボタンは、クリックで Win+F20、ダブルクリックで Win+F19 のキーコードを発行している。

なので AutoHotKey の設定に以下のような記述で、Win+F20キーとWin+F19 キーでの処理を記述すれば、Evernote で運用できる。  

```
 #F20::
 Run C:\Program Files (x86)\Evernote\Evernote\Evernote.exe /NewInkNote
 return
 #F19::
 Run C:\Program Files (x86)\Evernote\Evernote\Evernote.exe /Task:ClipScreen
 return
```
