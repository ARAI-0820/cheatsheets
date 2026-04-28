# Shell Stabilization

## Step 1: Spawn TTY
環境に合わせてどれか1つ実行。

Python3
```
python3 -c 'import pty;pty.spawn("/bin/bash")'
```
Python2
```
python -c 'import pty;pty.spawn("/bin/bash")'
```
Script 
```
script /dev/null -c /bin/bash
```
Perl 
```
perl -e 'exec "/bin/bash";'
```

## Step 2: Background & Raw Mode
`Ctrl + Z`
```
stty raw -echo; fg
```
`reset`

## Step 3: Variables
```
export TERM=xterm
```
