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