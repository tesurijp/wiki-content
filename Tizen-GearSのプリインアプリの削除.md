事前に [Root化](Tizen-GearSのroot化) 必須

例: Nike Running を削除する。

 - sdb root on
 - sdb shell
 - rm -rf /usr/apps/bNAm8uFvZ6 (消したいアプリの パッケージID)
 - rm -rf /opt/usr/apps/bNAm8uFvZ6 (消したいアプリの パッケージID)
 - exit
 - sdb pull /opt/usr/apps/com.samsung.w-home/data/apps_order.xml
 - sdb pull /opt/usr/apps/com.samsung.w-home/data/.apps.db
 - sdb pull /opt/usr/apps/com.samsung.w-home/data/.apps.db-journal
 - 適当なテキストエディタで、apps_order.xml から、 Nike Running(消したいアプリ)に関する apps タグを削る
 - .apps.db は SQLite のデータベースなので、適当な SQLiteエディタで編集
    - apps テーブルから、Nike Running(消したいアプリ) のレコードを削除
 - sdb push apps_order.xml /opt/usr/apps/com.samsung.w-home/data/
 - sdb push .apps.db /opt/usr/apps/com.samsung.w-home/data/
 - sdb push .apps.db-journal /opt/usr/apps/com.samsung.w-home/data/
 - Gear S を再起動
