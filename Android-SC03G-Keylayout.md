ご多分にもれず、SC03G のキーボードにも CAPS キーがある。
不要なので、これを CTRL にしてしまう

[klファイル](https://onedrive.live.com/download.aspx?cid=A212FD3B0AE0F943&resid=A212FD3B0AE0F943%21317262&canary=wisRQ%2FveGaWrk1tQ6rbNpLHsTUnZaDlvpBNk0K3PlT0%3D6&ithint=%2Ekl)

これを /system/usr/keychars/ に上書きして、キーボードを接続しなおすと、CAPSのランプの ON/OFF はそのままだが、CAPSロックはかからず、CTRL キーとして動作する。

上書きするさいにアクセス権の chmod 644 を忘れずに。
