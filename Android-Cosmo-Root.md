# CosmoCommunicatorのRoot化

おそらく、Planetから公式の Root化ファームが公開されると思われるが、それが待てない人向け  
当然、無保証  
壊れても知らない  

## 準備

### MTKドライバ

PlanetからGemini PDA用にMTKデバイス用のドライバが提供されているがCosmoの MTK6771に対応したバージョンではないので、よそから入手する。  
たとえば [ここ](https://androidmtk.com/download-mtk-driver-auto-installer)  
他社のMTKデバイス用に入れてたら、それが対応しているかもしれない。PCにつないで認識しなければ入れればいい。

### ADBドライバ

Googleのでも何でもいい。  
root化しようとする人のPCで入ってないことはないだろう。

入ってる ADBドライバがメーカー違いの物で互換性が確認できないなど自動で適用されない場合は、デバイスマネージャから「ドライバの更新」→「コンピュータを参照してドライバー〜」→「コンピューター上の利用可能な〜」で、メーカー違いでも ADBドライバを適用すれば良い。警告は出るが動作に問題はない(はず)

adb および、fastboot を使うので、そのあたりが動くように。


### バックアップ

こんな作業をするのに消えて困るデータがそのままってことは無いだろうけど念のため。

### 心構え

このページの情報が間違っていた、手順を間違えたなどの理由で、文鎮となっても自己責任だという覚悟  
最近のスマホは軽くなってしまったが、Cosmo は文鎮にも丁度いい重さになっている。

### Magisk化されたカーネルの用意

本来、bootイメージを吸い出してMagisked Patchをするのが筋なのだが、Patchされたboot.imgを公開してくているので、有り難く頂戴する。  
[こちらのポスト](https://www.oesf.org/forum/index.php?showtopic=35879&st=15&p=292918&#entry292918)

## 手順

1. 設定のビルド番号のタップを繰り返して、開発者モードを有効化

1. 開発者モードで、USBデバッグと OEM Unlock を有効化

1. PCについないで、adb reboot download (fastboot ではない)

1. downloadモードではなく fastbootで起動する。

1. PCにつないで fastboot でつながることを確認

1. fastboot flashing unlock (いらないかも)

1. fastboot flash boot boot-magisk .img

1. fastboot reboot

異常のあるカーネルなのでブートしない旨が表示されるなら、どこかが間違っている。  
一旦、オリジナルの boot.imgを焼き直して仕切り直す。

異常のあるカーネルなので、5秒後にブートするといった内容が表示されたら成功  
初回起動は、全データがフォーマットされるので時間がかかる。気長に待とう。

## ブート後

[ここ](https://github.com/topjohnwu/Magisk/releases/)から、Magisk Managerの apk をダウンロードしてインストール  
インストール後、Magisk が古いから更新とか言われるので適当にアップデート  

再起動するたびに、5秒後にブート〜のようなメッセージは出るが気にしない。

/systemの書き換えは出来ないらしく、ROM内アプリの削除はうまくいかない。
AdAway は、systemless設定を有効に。

