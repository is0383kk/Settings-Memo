# はじめに

本手順書では uv の使用方法を記載している。

## ■ 仮想環境の作成

下記コマンドで作業ディレクトリ配下に仮想環境用ディレクトリ「/.venv」を作成する。  
※仮想環境名は変更可能  
※Python のバージョンを pyenv などで導入した Python のバージョンに依存する  
（＝ **Python のバージョンを変更する場合は、pyenv などでバージョンを変更した上で uv で仮想環境を作成する**）

```powershell
uv venv .venv
```

作成した仮想環境は下記構成となっている

- 独立した Python 実行環境
- Scripts フォルダ（Windows の場合）： activate.ps1 や pip.exe など、その環境専用の実行ファイル
- site-packages： pip install したライブラリがここに入る
- pyvenv.cfg：Python 仮想環境の設定ファイル

```ini:pyvenv.cfg
home = C:\Users\ユーザ名\.pyenv\pyenv-win\versions\3.11.9
implementation = CPython
uv = 0.8.14
version_info = 3.11.9
include-system-site-packages = false
```

## ■ 仮想環境の有効化

下記コマンドで仮想環境を有効化する。  
※有効化すると「(.venv)」が表示される

```powershell
.\.venv\Scripts\Activate.ps1
```
