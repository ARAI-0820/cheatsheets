## よく使う辞書


簡易的なディレクトリ調査
```
/usr/share/wordlists/dirb/common.txt
```

大きいディレクトリ調査用辞書
```
/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```


最も頻繁に使われる5000個のサブドメイン
```
/usr/share/dnsrecon/dnsrecon/data/subdomains-top1mil-5000.txt
```


大きいサブドメイン辞書
```
/usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt
```

```
/usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt
```

## CEWL

cewl -d  -m  -w [作成したい辞書の名前] http://$IP

`-d` 何階層まで掘るか

`-m` 最低何文字にするか
