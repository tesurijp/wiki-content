いつのバージョンからか不明だが、改造された(root化含む)端末で AmazonPrimeVideo を再生しようとすると DECRYPTION FAILURE が表示されて再生できなくなっている。  
この場合 /system/lib/liboemcrypto.so がロードされないようにすることで再生できるようになる。
```
mv /system/lib/liboemcrypto.so  /system/lib/liboemcrypto.so.bak
``` 