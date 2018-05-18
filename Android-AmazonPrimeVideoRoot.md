いつのバージョンからか不明だが、改造された(root化含む)端末で AmazonPrimeVideo を再生しようとすると DECRYPTION FAILURE が表示されて再生できなくなっている。  
この場合 /system/lib/liboemcrypto.so が読込まれないようにすることで再生できるようになる。
```
mv /system/lib/liboemcrypto.so  /system/lib/liboemcrypto.so.bak
``` 
アプリを動かした後など、すでに読込まれている場合、名前を変更しても読込まれていることに変わりはないので端末の再起動を行なっておくのが無難

環境によっては、/system/lib がループバックデバイスになっており、自由に削除できないケースがある。  
その場合は、以下のようなスクリプトを作成し、Tasker や Macrodroid で端末起動時をトリガーに呼び出す。
```
#!/system/bin/sh
/system/bin/umount /system/lib/liboemcrypto.so
/system/bin/rm /system/lib/liboemcrypto.so
``` 
起動直後に動かすと、マウント処理が完了していないケースもあるので、起動直後から30秒か1分程度待機したタイミングで呼び出すのが望ましい。
