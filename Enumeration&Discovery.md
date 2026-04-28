Enumeration & Discovery Cheat Sheet
1. Port Scanning (ポートスキャン)

ターゲットでどのサービスが動いているかを高速に調査します。
RustScan

Nmapを内部で呼び出す、非常に高速なポートスキャナーです。
Bash

rustscan -a $IP -- -sV -sC

    解説: まずRustScanが全ポートを高速スキャンし、開いているポートに対してのみNmapの詳細スキャン（-sV: バージョン特定、-sC: 標準スクリプト実行）を行います。

    おすすめオプション:

        -r 1-65535: 全ポートを対象にする（デフォルトで漏れがないように）。

        --ulimit 5000: 接続の同時制限数を上げ、さらに高速化する。

2. Web Directory Discovery (ディレクトリ探索)

隠しページや管理パネルを見つけるためのツールです。
GoBuster

Go言語製で非常に高速なディレクトリ・ファイル探索ツールです。
Bash

gobuster dir -u http://$IP -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt

    解説: 辞書ファイル（Wordlist）を使って、URLの後ろに続くディレクトリ名をしらみつぶしに探します。

    おすすめオプション:

        -x php,txt,html: 指定した拡張子のファイルも同時に探します。

        -t 50: スレッド数を増やして高速化（サーバーへの負荷に注意）。

3. Fuzzing (ファジング)

パラメータやディレクトリなど、あらゆる場所を「FUZZ（変動する値）」としてテストします。
ffuf / wfuzz / dirsearch

    ffuf: 現在最も人気のある高速ファザー。

        ffuf -u http://$IP/FUZZ -w [Wordlist]

    wfuzz: 柔軟性が高く、複数の場所を同時にファズするのに向いています。

    dirsearch: Python製で、インストール不要で使いやすく、結果が色分けされて見やすいのが特徴。

4. Vulnerability Scan (脆弱性スキャン)

既知の脆弱性や設定ミスを自動でチェックします。
Nikto

Webサーバーの古いバージョンや、危険なファイル、設定ミスをスキャンします。
Bash

nikto -h http://$IP

    解説: Webサーバー全般の「低くぶら下がった果実（簡単に取れる脆弱性）」を探すための定番ツールです。

WhatWeb

Webサイトが使っているCMS（WordPressなど）やライブラリ、サーバーの種類を特定します。
Bash

whatweb http://$IP

5. SMB Enumeration (SMB情報の列挙)

WindowsやLinuxの共有フォルダ（ポート445）が開いている場合に使用します。
enum4linux-ng

SMB共有からユーザー名、共有フォルダ、OS情報などを抜き出す次世代ツールです。
Bash

enum4linux-ng -A $IP

    解説: 以前の enum4linux をPythonで書き直したもので、出力が非常に読みやすくなっています。-A は「すべて実行」を意味します。

6. 特定パターンの探索（ユーザーディレクトリ等）
GoBuster Fuzzモード
Bash

gobuster fuzz -w [Wordlist] -u http://$IP/~FUZZ -b 404

    解説: URLの途中（この例では ~ の後ろ）をファズします。

    おすすめオプション:

        -b 404,403: 特定のステータスコード（404 Not Foundや403 Forbidden）を除外して表示します。
