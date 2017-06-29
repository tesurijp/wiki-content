# Windows 上で VMWare を DockerMachine にして Docker を使う

Windows 上でDocker を使うには Docker For Windows を使うのが一番簡単で、なおかつ Windows コンテナも使えるのだが個人的な都合で VMWare を使いたいので設定メモ

## 手順
1. VMWare をインストール
1. [DockerToolbox](https://www.docker.com/products/docker-toolbox) をインストール  
コマンドラインから、引数を付けて起動すれば、Virtual Box を入れないように出来る  
```DockerToolbox /COMPONENTS="Docker,DockerMachine```
1. [VMWare用の docker-machine-driver](https://github.com/pecigonzalo/docker-machine-vmwareworkstation)を追加  
docker-machine-driver-vmwareworkstation.exe を DockerToolbox のインストールフォルダにコピーする  
VMWare用の docker-machine-driver の ReadMe にスクリプトの修正されたスクリプトがあるが起動のたびに VM を作り直すような構造なので使いにくい。  
環境は別途用意する。  
1. default VM の作成  
```docker-machine create --driver=vmwareworkstation default```
1. vmx ファイルの修正  
VMWare では標準的に作成される VM は、ログ、メモリの状態などディスクへのアクセスが常時発生、VM側のメモリも勝手に調整するとか異常に重い設定になっている。
対象のファイルは ```%USERPROFILE%\.docker\machine\machines\default\default.vmx```  
ファイルをテキストエディタで開いて、末尾に追加する。  
この修正は、VM を終了した状態で修正する。  
VM が起きているときにファイルを修正した場合は、VM 終了時に元の設定に戻される。  
    ```
    MemTrimRate = "0"
    mainMem.useNamedFile= "FALSE"
    sched.mem.pshare.enable = "FALSE"
    prefvmx.useRecommendedLockedMemSize = "TRUE"
    MemAllowAutoScaleDown = "FALSE"
    logging = "FALSE"
    ```
1. 実行環境  
標準のスクリプトでは、msys や git for windows の bash を使うようgit for windows や MSYS PowerShell を使ったほうが快適なので、PowerShell 用の環境にする