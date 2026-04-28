## Steganography


## 基本解析コマンド

- `file [file]`　# ファイル形式を特定
- `strings [file] | head -n 20`　# 冒頭の可読文字列を20行表示
- `strings [file] | tail -n 20`　# 末尾の可読文字列を20行表示
- `strings -n 8 [file]` 　　　　 # 8文字以上の連続した文字列のみを表示
- `hexdump -C [file] | head`    # バイナリのヘッダ部分を確認


### steghide
隠されたデータを取り出す
- `steghide extract -sf [imagefile] -p [passwd]` # パスワードを指定してファイルを抽出
- `steghide info [imagefile]`   # 埋め込まれた情報の有無を確認

### binwalk
ファイルの中に別のファイルが隠されていないかスキャン・抽出する。
- `binwalk [file]`   # 中身を確認
- `binwalk -e [file]`  # 隠されたファイルを自動抽出

### exiftool
画像やPDFのメタデータを確認する
- `exiftool [file]` # メタデータを表示

- 
