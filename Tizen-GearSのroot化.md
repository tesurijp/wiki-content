XDA にも書いたけど日本語でも記録

 - Gear S のファームを拾ってくる
 - tar.md5 の展開
 - その中の rootfs.img を Linux 等 ext4 のイメージをマウントできる環境で編集する
      - su ${mountfolder}/bin/su
      - chmod 755 ${mountfolder}/bin/su
      - cp vconf-init ${mountfolder}/etc/rc.d/init.d/vconf-init
      - chmod 755 ${mountfolder}/etc/rc.d/init.d/vconf-init
      - cp rc.local.service ${mountfolder}/etc/systemd/system
 - rootfs.img をアンマウント
 - tar -H ustar -c rootfs.img > rootfs.img.tar
 - md5sum rootfs.img.tar >> rootfs.img.tar
 - mv rootfs.img.tar rootfs.img.tar.md5
 - Gear S の ボタンを再起動するまで押しつづける
 - reboot メッセージが出たらボタンを一旦離して、もう一度押す
 - ダウンロードモードを選択(ボタン押下で候補の移動、長押しで選択)
 - odin で 作った rootfs.img.tar.md5 をやく
