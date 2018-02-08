いつのバージョンからか不明だが、改造された(root化含む)端末で AmazonPrimeVideo を再生しようとすると DECRYPTION FAILURE が表示されて再生できなくなっている。  
この場合 /system/lib/liboemcrypto.so が読込まれないようにすることで再生できるようになる。
```
mv /system/lib/liboemcrypto.so  /system/lib/liboemcrypto.so.bak
``` 
アプリを動かした後など、すでに読込まれている場合、名前を変更しても読込まれていることに変わりはないので端末の再起動を行なっておくのが無難
