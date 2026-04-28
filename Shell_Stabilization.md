# Shell Stabilization

## Step 1: Spawn TTY
環境に合わせてどれか1つ実行。

- **Python3 (基本):** `python3 -c 'import pty;pty.spawn("/bin/bash")'`
- **Python2:** `python -c 'import pty;pty.spawn("/bin/bash")'`
- **Script (汎用):** `script /dev/null -c /bin/bash`
- **Perl:** `perl -e 'exec "/bin/bash";'`

## Step 2: Background & Raw Mode
1. `Ctrl + Z`
2. `stty raw -echo; fg`
3. `reset` (必要な場合。画面が崩れたら実行)

## Step 3: Variables
- `export TERM=xterm
