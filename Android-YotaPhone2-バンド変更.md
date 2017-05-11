ホームキー長押しから YotaMirror が起動できるが、別のところからもショートカットで起動したかったり、標準のナビバー使わないと、そもそも呼び出せない。  
というわけで、呼び出す方法を確認してみた。  

具体的には以下のインテントをブロードキャストすればよい。  
```
yotaphone.intent.action.MIRRORING_START
```  
Tasker とかで、このインテントを投げるTask 作成すればよい。  
Ultimate Dynamic Navbar から呼び出すには Tasker App Factory でアプリ化してしまえば問題なし。