RealmsWiki に移行してみたのだが、コンテンツ管理の中に画像ファイル等が置けない。  
RealmsWiki 自身にリクエストが投げられると、拡張子が何であれページとして認識されてしまうようだ  

テキストと画像を別で管理しても良いのかもしれないが、それはとてつもなく扱いずらい。
コンテンツそのものは一箇所にまとめて管理したいので nginx 側で画像の時には RealmsWiki に投げないようにしてみた。

```
server {
        listen 443 ssl;
        server_name wiki.tesuri.org;

        location ~ .*\.(jpg|jpeg|gif|png) {
            root /path/to/wiki/contents/;
        }
        location / {
            proxy_pass http://realmswiki;
        }
}
```

通常のリクエストは upstream で RealmsWiki のポートにつないでいる。  
拡張子が、jpg/jpeg/gif/png のリクエストは、wiki コンテンツページに静的につなぐ。  
path/to/wiki/contents は RealmsWiki も見ているコンテンツのあるフォルダ  
