# Windows 上で VMWare を DockerMachine にして Docker を使う

Windows 上でDocker を使うには Docker For Windows を使うのが一番簡単で、なおかつ Windows コンテナも使えるのだが個人的な都合で VMWare を使いたいので設定メモ

## 手順
1. VMWare をインストール

1. [DockerToolbox](https://www.docker.com/products/docker-toolbox) をインストール  
コマンドラインから、引数を付けて起動すれば、Virtual Box を入れないように出来る  
```DockerToolbox /COMPONENTS="Docker,DockerMachine```

1. [VMWare用の docker-machine-driver](https://github.com/pecigonzalo/docker-machine-vmwareworkstation)を追加  
docker-machine-driver-vmwareworkstation.exe を DockerToolbox のインストールフォルダにコピーする  
スクリプトは修正しなくていい。  
docker-machine-driver-vmwareworkstation の ReadMe にVMWare 用に修正されたスクリプトも用意されているが、こちらは起動のたびにVMを作り直すなど常用しづらい。
環境は別途用意する。  

1. default VM の作成  
```docker-machine create --driver=vmwareworkstation default```

1. vmx ファイルの修正  
VMWare では標準的に作成される VM は、ログ、メモリの状態などディスクへのアクセスが常時発生、VM側のメモリも勝手に調整するとか異常に重い設定になっていて使いずらいnのdので修正する。  
対象のファイルは ```%USERPROFILE%\.docker\machine\machines\default\default.vmx```  
ファイルをテキストエディタで開いて、末尾に追加する。この修正は、VM を終了した状態で修正する。  
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
    1. [Docker for Powershell](https://github.com/Microsoft/Docker-PowerShell) のインストール
        ```
        Register-PSRepository -Name DockerPS-Dev -SourceLocation https://ci.appveyor.com/nuget/docker-powershell-dev
        Install-Module -Name Docker -Repository DockerPS-Dev -Scope CurrentUser
        ```
    1. Docker VM の起動は、PowerShell に特別用意されているわけではないので ```docker-machine start```  
    
    1. Docker VM が動いている状態で ```docker-machine.exe env | Invoke-Expression```  
    
    docker コマンドのかなりの部分は Cmdlet が用意されてるようだが完全ではない。docker コマンドも使う
    
