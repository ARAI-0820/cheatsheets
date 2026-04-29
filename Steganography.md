## Steganography


## 基本解析コマンド

- `file [file]`　# ファイル形式を特定
- `strings [file] | head -n 20`　# 冒頭の可読文字列を20行表示
- `strings [file] | tail -n 20`　# 末尾の可読文字列を20行表示
- `strings -n 8 [file]` 　　　　 # 8文字以上の連続した文字列のみを表示
- `hexdump -C [file] | head`    # バイナリのヘッダ部分を確認

### hexeditor

バイナリが書き換えられていたらhexeditorで修正する

`hexeditor [file]`

修正が終わったらCtrl + O 　→　　Enter　→　　Ctrl + X

#### マジックナンバー

.png	`89 50 4E 47 0D 0A 1A 0A`	  .PNG....

.jpg	`FF D8 FF E0 (または E1, DB)`	ÿØÿà

.gif	`47 49 46 38 39 61 (または 37a)`	GIF89a

.zip	`50 4B 03 04`	  PK..

.pdf	`25 50 44 46`	  %PDF

ELF実行ファイル	(Linux)	`7F 45 4C 46`	.ELF

.class	`CA FE BA BE`

RAR圧縮	.rar	`52 61 72 21 1A 07`	Rar!..

7-Zip圧縮	.7z	`37 7A BC AF 27 1C`	  7z..'.



### steghide
隠されたデータを取り出す
- `steghide extract -sf [file] -p [passwd]` # パスワードを指定してファイルを抽出
- `steghide info [file]`   # 埋め込まれた情報の有無を確認

### binwalk
ファイルの中に別のファイルが隠されていないかスキャン・抽出する。
- `binwalk [file]`   # 中身を確認
- `binwalk -e [file]`  # 隠されたファイルを自動抽出

### exiftool
画像やPDFのメタデータを確認する
- `exiftool [file]` # メタデータを表示
