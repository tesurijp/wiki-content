Gear S からは、開発者署名を行なう必要があり、wgt のサイドロードは出来なくなっています。

## アプリのサイドロード
Android と同様に マーケット外からでもアプリをサイドロードでインストールできます。  
配布されるフォーマットは .wgt です。(拡張子を ZIP に変えれば中身を見ることも出来ます)

サイドロードには Tizen SDK が必要です。
正確には Tizen SDK をインストールしたフォルダにある  tools/sdb.exe が必要です。  
[sdb.zip](/image/SideLoad/sdb.zip)  
android の adb.exe に相当するようで、機能も近いものがあります。  

Gear 端末の [設定]-[Gearの情報]-[USBデバッグ] という設定があるので、これを ON にします。
この状態で、PC に接続すると sdb での接続が可能です。

## インストール
インストールを行なうには、wgt のパッケージを持ってきて  
``sdb install [パッケージファイル]``  
とするだけです。

## アンインストール
アンインストールは少し厄介です。  
ソフトウェアのパッケージID が必要ですが、TizenSDK で作成してみる限りでは ランダムに決まってしまう(？)ものらしく、作者自身も意識していない可能性があります。

ともあれ、パッケージID が判っている場合は、  
``sdb uninstall [パッケージID]``  
でアンインストールできます。  

パッケージIDが不明な場合は、インストールした wgt ファイルの中から探すことが出来ます。  
拡張子を .zip にして展開すると中に config.xml というファイルが入っています。  
このファイル内の tizen:application タグに書かれた package アトリビュートがそのアプリのパッケージIDとなります。

config.xml が以下のような内容であれば、パッケージID は j42qKnjujT ということになります。

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <widget xmlns:tizen="http://tizen.org/ns/widgets"  xmlns="http://www.w3.org/ns/widgets" id="http://yourdomain/basic"  version="1.0.0" viewmodes="maximized">
     <tizen:application id="j42qKnjujT.basic" package="j42qKnjujT"  required_version="2.2"/>
     <content src="index.html"/>
     <feature name="http://tizen.org/feature/screen.size.all"/>
     <icon src="icon.png"/>
     <name>basic</name>
 </widget>
 ```
