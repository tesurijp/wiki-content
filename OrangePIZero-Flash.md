RasPI も含めメインストレージが SD(micorSD) な環境を常時稼動させると、かなりの頻度で壊れる。  
どちらにしろ定期的に交換するのが安全なのだが、少しでも壊れにくくするためには書き込みの頻度を下げる必要がある。

## / パーティション
パーティションのマウウントオプションに 
```
UUID=XXXXXXXX / ext4 defaults,noatime,nodiratime,commit=600,errors=remount-ro 0 1
```
noattime、 nodiratime は、PC とかでも使うことがあるが、普通の PC では滅多にやらない commit=600 を付与する  
sync の周期を 600秒(10分)ごとになる。  PC でも SSD だとやるかも

## tmp および /var/tmp
もちろん tmpfs にする。

## /var/log
これも tmpfs にする。  
再起動で消えると困るので shutdown 時に backup、起動時に restoreする  
/etc/init.d に以下のようなスクリプトを追加
```
#!/bin/bash
#
### BEGIN INIT INFO
# Provides:          loginit
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Required-Start:
# Required-Stop:
# Short-Description: Create /var/log/... files on tmpfs at startup
# Description:       Create /var/log/... files needed by system daemon
### END INIT INFO
.
#
# main()
#

ck_file="/var/lock/subsys/loginit"

case "${1:-''}" in
  'start')
    cp -av /var/logback/* /var/log
    touch ${ck_file}
   ;;
  'stop')
    cp -av /var/log/* /var/logback/
    rm -r ${ck_file}
   ;;
  'restart')
   ;;
  'reload'|'force-reload')
   ;;
  'status')
   ;;
  *)
   echo "Usage: $SELF start"
   exit 1
   ;;
esac
```
サービスの最初の方に起動させる。  
同様に cron で rsync バックアップも入れる  

うちの環境では、softether もOrangePI で稼動させている。  
softether は、設定ファイルを更新しつづけるので、/var/log と同様、起動時に tmpfs にコピーした上で実行するようにしている。