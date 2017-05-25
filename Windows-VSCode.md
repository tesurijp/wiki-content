## Visual Studio Code
### 設定の共有

複数のPC を利用している環境での、Visual Studio Code の設定共有方法  
OneDrive で行なっているが、Dropbox 等でも同じ。  
- 拡張機能は %USERPROFILE%\.vscode にインストールされているので、これを OneDriveの管理下に**移動**  
- %USERPROFILE%\.vscode から、移動した OneDrive 下のフォルダへシンボリックリンクを作成  
- 設定情報は%AppData%\Code\User に保存されているので、こちらも OneDriveの管理下に**移動**
- %AppData%\Code\User から、移動した OneDrive 下のフォルダへシンボリックリンクを作成  

同時に更新(両方のPC から同時に同じ拡張機能を更新する)するような事が無ければ、両方のPC を同時に使っていても問題ない。