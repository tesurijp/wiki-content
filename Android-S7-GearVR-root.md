Galaxy S7で rooted 環境で GearVR を使う

root 化した環境に GearVR を買ってきて繋いでも ネットワークエラーとなって使えない。

odin で stock rom をやきなおしたり、Factory Reset しても駄目。  
一旦 root 化した端末では、SmartSwitch を使ったリカバリを行なわなければ GearVR が使えるようにはならない。

rooted 端末で拒否されるのは GearVR の初回起動時のチェックのみらしく、GearVR を接続して必要なアプリ群がインストールされた後、root 化を行なえば、GearVR が使える状態のまま root 環境も使えている。  
Oculus Store からのアプリインストールも確認できた。

## すでに root 化してしまっている場合
SmartSwitch でリカバリが必要

 - 完全に初期化するので、必要なデータ類はバックアップ。
 - PC用の SmartSwitch をインストール (http://www.samsung.com/jp/support/smartswitch/#pc_version)
 - SmartSwitch 上で、PC と Galaxy を接続し、ドライバ類が入っていることを確認
 - USBケーブルをぬいて、端末がつながっていない状態にする
 - SmartSwitch のメニュー(「その他」と書いてるやつ)から、「緊急ソフトウェアリカバリーと初期化」を開く
 - 「端末の初期化」タブで、モデル名 ( SM-G930FD とか、SM-G930F とか )を入力して、検索ボタン
 - S/N の入力欄が出てくるので、S/N を入力して確認ボタン。
 - 確認メッセージが何度か出るので、最後に  Galaxy を ダウンロードモード(電源OFF 状態から VolDown + HOME + 電源ON)にして接続
 - Frimware のダウンロードが始まる(かなり時間かかる) 

初期化されたら、データのリカバリは後回しにして、GearVR を接続し、画面の指示に従って GearVR が使えるようになっていることを確認する。

## root化
Gear VR を使える状態で root化する方法

TWRP のスレッドだと、TWRP の初回起動時に、/data を wipe するように書かているが、これは実施すると GearVR にインストールされたアプリが削除されてしまうのでと共存が出来なくなる。
wipe しないと、TWRP から /data や /sdcard などを見ることが出来ないが、root 化や Xposed を使えるようにするぶんには不要。
/sdcard が TWRP から見えないので、適用する ZIP は microSD に入れておく必要がある。

- 開発者 モードを有効化
- 開発者モードの設定で、OEM unlock を許可
- ODINで twrp をやく( http://forum.xda-developers.com/galaxy-s7/development/recovery-official-twrp-herolte-t3333770 )
- twrp を起動して、以下の ZIP を*順*に適用。途中で再起動すると S7 が起動しなくなるケースもあるので注意  
  /data のマウントができないエラーは無視   
 - SuperSU の ZIP を適用( https://download.chainfire.eu/932/SuperSU/BETA-SuperSU-v2.71-20160331103524.zip)
 - dm-verity-opt-encrypt.zip を適用 ( https://idlekernel.com/fun-stuff-trust-me/no-verity-opt-encrypt.zip )
 - xposed の ZIP を適用(http://forum.xda-developers.com/xposed/unofficial-xposed-samsung-lollipop-t3180960) (xposed が不要ならいらない)
 - dm-verity-opt-encrypt.zip を再度適用 (xposed が不要ならいらない)
- 再起動
- 時間がかかるがしばらく待機

