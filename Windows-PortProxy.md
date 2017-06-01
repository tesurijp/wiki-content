## Windows 端末のPortForward
Windows 端末が VPN クライアントになっているなど、Windows のPC をゲートウェイ化したいことがある。  
ルータもかねていれば、ルータにしてしまえば良いのだが、通常のネットワークとは異なる先へのゲートウェイになってほしい場合は、PortForward するのが便利
### 必要なサービス
IP Helper   
余計な事をするサービスなので、殺している場合もあるが、PortForward するためには有効にしておく必要がある。
### 設定方法
```bat
netsh interface portproxy add v4tov4 listenport=[localport] listenaddr=[localIP] connectport=[RemortPort] connectaddress=[RemoteIP]
```
localport は、他のPCから接続を受けるポート番号  
localIP は、他のPCから接続を受けるIPアドレス  
RemotePort は、接続したいサービスのポート番号  
RemoteIP は、接続したいサービスを実行しているPCのIP  

たとえば、LAN のネットワーク内でのアドレスが、191.168.0.100 、VPN 接続でのみ見えているサーバーのアドレスが 191.168.10.100 とする。  
サーバーの SSH は普通に 22 番で開いているとすると、こんな感じになる。  
```bat
netsh interface portproxy add v4tov4 listenport=123 listenaddr=191.168.0.100 connectport=22 connectaddress=192.168.10.100
```
受け口の ポート番号は空いてるものなら何でもよい。123 は適当  
こうして設定しておくと、LAN 内の他の PC から 191.268.0.100:123 に ssh すると、VPN先の 191.268.10.100:22 に sshつないだことになる。  
各マシンが VPN 接続できれば無用だが、VPN クライアントが1台しか設定できない場合に、接続を共有したいときには便利
もちろん FireWall 等で、接続を許可する必要はある。

現在設定されている PortForward の一覧は以下で確認  
```bat
netsh interface portproxy show all
```

Windows を再起動しても設定は消えない。 間違ったり不要になった設定の削除は以下  
```
netsh interface portproxy delete v4tov4 listenport=[localport]
```
