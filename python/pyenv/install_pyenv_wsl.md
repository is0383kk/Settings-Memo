# はじめに

本手順書では WSL 上に pyenv 環境を構築する手順について説明する

## ■ 前提

下記が導入済みであること

- wsl\install_wsl.md の手順に従い WSL 環境が構築済みであること

### 参考

- https://github.com/pyenv/pyenv

# １．pyenv を導入する

## ■ pyenv のインストール

下記コマンドで pyenv をインストールする

```bash
$ curl -fsSL https://pyenv.run | bash
Cloning into '/home/ユーザ名/.pyenv'...
remote: Enumerating objects: 1433, done.
・・・
Receiving objects: 100% (64/64), 43.19 KiB | 3.32 MiB/s, done.
Resolving deltas: 100% (10/10), done.
```

## ■ pyenv の環境変数設定

`~/.bashrc` への環境変数を追加する

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init - bash)"' >> ~/.bashrc
```

`~/.profile` への環境変数を追加する

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.profile
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.profile
echo 'eval "$(pyenv init - bash)"' >> ~/.profile
```

`~/.bash_profile` への環境変数を追加する

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(pyenv init - bash)"' >> ~/.bash_profile
```

環境変数設定を下記コマンドで反映する

```bash
exec "$SHELL"
```

最後に pyenv コマンドの確認をする

```bash
$ pyenv --version
pyenv 2.6.8
```

## ■ Python ビルド用パッケージの最新化

Python をインストールする際に必要なビルド用パッケージを最新化する

```bash
$ sudo apt update
$ sudo apt install -y build-essential
```

```bash
sudo apt install -y \
  libssl-dev \
  zlib1g-dev \
  libbz2-dev \
  libreadline-dev \
  libsqlite3-dev \
  libffi-dev \
  liblzma-dev \
  tk-dev \
  wget curl llvm \
  make
```

### 補足：上記実行しなかった場合

ビルド用パッケージをダウンロードしなかった場合、ビルドエラーとなった

```bash
$ pyenv install 3.11.9
Downloading Python-3.11.9.tar.xz...
-> https://www.python.org/ftp/python/3.11.9/Python-3.11.9.tar.xz
Installing Python-3.11.9...

BUILD FAILED (Ubuntu 24.04 using python-build 2.6.8)

Inspect or clean up the working tree at /tmp/python-build.20251003195620.2214
Results logged to /tmp/python-build.20251003195620.2214.log

Last 10 log lines:
checking for pkg-config... no
checking for --enable-universalsdk... no
checking for --with-universal-archs... no
checking MACHDEP... "linux"
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: in `/tmp/python-build.20251003195620.2214/Python-3.11.9':
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details
```

## ■ Python のインストール

下記コマンドでインストール可能な Python のバージョンを確認できる

```bash
pyenv install --list
```

インストールしたい Python のバージョンを指定してインストールする

```bash
$ pyenv install 3.10.14
Downloading Python-3.10.14.tar.xz...
-> https://www.python.org/ftp/python/3.10.14/Python-3.10.14.tar.xz
Installing Python-3.10.14...
Installed Python-3.10.14 to /home/is0383kk/.pyenv/versions/3.10.14
```

インストール後グローバル指定する

```bash
pyenv global 3.10.14
```

グローバル指定した Python のバージョンが表示されることを確認する

```bash
$ python --version
Python 3.10.14
```
