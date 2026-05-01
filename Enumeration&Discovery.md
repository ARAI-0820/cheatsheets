# Enumeration & Discovery


### 1. Port Scanning

```
rustscan -a $IP -- -sV -sC
```

` -r 1-65535` 全ポートを対象にする


### 2. Web Directory Discovery

```
gobuster dir -u http://$IP -w [wordlist]
```

#### よく使う辞書

```
/usr/share/wordlists/dirb/common.txt
```

```
/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```



`-x php,txt,html` 指定した拡張子のファイルも同時に探索

`-t 50` スレッド数を増やして高速化

### 3. Fuzzing

`ffuf -u http://$IP/FUZZ -w [Wordlist]`

#### ffufオプション

隠しサブドメインを探すとき
`-H "Host: FUZZ.ドメイン"`

`wfuzz -c -z file,[wordlist] http://TARGET/FUZZ`

#### wfuzzオプション

`--hc`		指定したステータスコードを隠す（例: --hc 404）

`--sc`	    指定したステータスコードのみ表示（例: --sc 200）

`--hl`		指定した「行数」の結果を隠す

`--hw`		指定した「単語数」の結果を隠す

`--hh`		指定した「文字数」の結果を隠す


### 4. Vulnerability Scan


```
nikto -h http://$IP
```


```
whatweb http://$IP
```

### 5. Vulnerability Research

#### Service/CMS Version Identified

Searchsploit:  `searchsploit [Name] [Version]`

Google Search: `"[Name] [Version] exploit"` or `"CVE-[Year]-[ID]"`

GitHub:        `"[Name] [Version] PoC"`

####  CMS Specific
WordPress: `wpscan --url [URL] --enumerate vp` (脆弱なプラグイン調査)

Joomla:    `joomscan -u [URL]`


### 6. SMB Enumeration

```
enum4linux-ng -A $IP
```
