ご多分にもれず、SC03G のキーボードにも CAPS キーがある。
不要なので、これを CTRL にしてしまう

[klファイル](/image/SC03G/Vendor_04e8_Product_a006.kl)

これを /system/usr/keychars/ に上書きして、キーボードを接続しなおすと、CAPSのランプの ON/OFF はそのままだが、CAPSロックはかからず、CTRL キーとして動作する。

上書きするさいにアクセス権の chmod 644 を忘れずに。
