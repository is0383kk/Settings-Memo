# はじめに

本手順書では Windows11 上の WSL2 への npm の導入手順について説明する。

# nvm、node.js、および npm をインストールする

## ■ nvm のインストール

### １．cURL のインストール

下記コマンドで cURL をインストールする。

```bash
$ sudo apt-get install curl
```

### ２．nmv のインストール

下記コマンドで nvm をインストールする

```bash
$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 16631  100 16631    0     0  71634      0 --:--:-- --:--:-- --:--:-- 71685
=> Downloading nvm from git to '/home/hoge/.nvm'
=> Cloning into '/home/hoge/.nvm'...
remote: Enumerating objects: 383, done.
remote: Counting objects: 100% (383/383), done.
remote: Compressing objects: 100% (326/326), done.
remote: Total 383 (delta 43), reused 178 (delta 29), pack-reused 0 (from 0)
Receiving objects: 100% (383/383), 392.12 KiB | 8.17 MiB/s, done.
Resolving deltas: 100% (43/43), done.
* (HEAD detached at FETCH_HEAD)
  master
=> Compressing and cleaning up git repository

=> Appending nvm source string to /home/hoge/.bashrc
=> Appending bash_completion source string to /home/hoge/.bashrc
=> You currently have modules installed globally with `npm`. These will no
=> longer be linked to the active version of Node when you install a new node
=> with `nvm`; and they may (depending on how you construct your `$PATH`)
=> override the binaries of modules installed with `nvm`:

C:\Users\hoge\AppData\Roaming\nvm\v22.16.0
+-- @openai/codex@0.20.0
+-- corepack@0.32.0
=> If you wish to uninstall them at a later point (or re-install them under your
=> `nvm` node installs), you can remove them from the system Node as follows:

     $ nvm use system
     $ npm uninstall -g a_module

=> Close and reopen your terminal to start using nvm or run the following to use it now:

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

### ３．環境変数の反映

インストール完了後、下記コマンドで nvm の環境変数を反映させる

```bash
source ~/.bashrc
```

### ４．nvm の動作確認

下記コマンドで nvm コマンドが実行できるか確認する

```bash
$ nvm --version

0.40.3
```

※下記のように表示された場合、環境変数が反映されていない可能性がある

```bash
$ nvm --version
Command 'nvm' not found, did you mean:
  command 'lvm' from deb lvm2 (2.03.16-3ubuntu3.2)
  command 'nvme' from deb nvme-cli (2.8-1ubuntu0.1)
  command 'kvm' from deb qemu-system-x86 (1:8.2.2+ds-0ubuntu1.6)
  command 'nm' from deb binutils (2.42-4ubuntu2.4)
Try: sudo apt install <deb name>
```

## ■ node.js のインストール

下記コマンドで node.js の LTS リリースをインストールする

```
$ nvm install --lts
Installing latest LTS version.
Downloading and installing node v22.18.0...
Downloading https://nodejs.org/dist/v22.18.0/node-v22.18.0-linux-x64.tar.xz...
################################################################################################################# 100.0%
Computing checksum with sha256sum
Checksums matched!
Now using node v22.18.0 (npm v10.9.3)
Creating default alias: default -> lts/* (-> v22.18.0)
```

インストール後、下記コマンドでインストールされた node.js のバージョンを確認する

```bash
$ node --version
v22.18.0
```
