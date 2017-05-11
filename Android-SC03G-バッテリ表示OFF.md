SC-03G では、設定のバッテリーメニューに 残量表示の有無を選択するチェックボックスがないが、[アイコンに数字を重ねる](Android-Kitkat-バッテリ表示)ようにしていると表示の重複もあるので不要  
```
 content insert --uri content://settings/system --bind name:s:display_battery_percentage --bind value:i:0
```
を実行して再起動
```
 content insert --uri content://settings/system --bind name:s:display_battery_percentage --bind value:i:1
```
で表示を復元
