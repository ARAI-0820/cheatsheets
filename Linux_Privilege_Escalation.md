## OSバージョンとカーネル情報の確認

`uname -a`


## 現在のユーザーのグループ所属確認
### 'docker', 'lxd', 'disk', 'video' グループに属していないか

`id`


## sudo権限の確認

`sudo -l`


## SUIDファイルの探索

`find / -perm -4000 -type f 2>/dev/null`


## Capabilitiesの確認

`getcap -r / 2>/dev/null`


## Cronの設定ファイル確認

`cat /etc/crontab`
`ls -la /etc/cron.d/`
`systemctl list-timers --all`  # systemdのタイマーを確認



## アーキテクチャの確認
#### x86_64 なら 64bit
#### i386, i686 なら 32bit

`uname -m`

## archコマンド
#### 出力が 'x86_64' 以外（i686など）なら 32bit
`arch`

## プロセス・ジョブのリアルタイム監視
#### -pf: プロセスとファイルイベントを表示, -i: スキャン間隔(ms)

`./pspy64 -pf -i 1000`
`./pspy32 -pf -i 1000`


## linpeas

./linpeas.sh
