KitKat 化した SC02F での root 取得のメモ
- ODINでCWM をやく( http://sakuraba-android.blogspot.jp/2014/07/sc02f-kk-cwmtarmd5.html )
- UPDATE-SuperSU-v2.01.zip を適用( http://download.chainfire.eu/451/SuperSU/ )
- 通常起動。おサイフが死んでることを確認
- ODIN で Stock recovery をやく
- 起動。おサイフが復活していることを確認
- dd recovery.img を dd で書き込む 
```
dd if=/sdcard/recovery.img of=/dev/block/mmcblk0p15
```
- リカバリを起動。CWM が動くことを確認
- 通常起動。オサイフが活きていることを確認
