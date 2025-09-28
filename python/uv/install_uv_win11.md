# はじめに

本手順書では Windows11 上に uv／uvx をインストールする手順について説明する。

## ■ uv／uvx の導入

下記コマンドで uv／uvx を導入する。

```powershell
powershell -ExecutionPolicy Bypass -c "irm https://astral.sh/uv/install.ps1 | iex"
Downloading uv 0.8.14 (x86_64-pc-windows-msvc)
Installing to C:\Users\ユーザ名\.local\bin
  uv.exe
  uvx.exe
  uvw.exe
everything's installed!

To add C:\Users\ユーザ名\.local\bin to your PATH, either restart your shell or run:

    set Path=C:\Users\ユーザ名\.local\bin;%Path%   (cmd)
    $env:Path = "C:\Users\ユーザ名\.local\bin;$env:Path"   (powershell)
```

その後、下記コマンドでパスを通す。

```powershell
$env:Path = "C:\Users\ユーザ名\.local\bin;$env:Path"
```

下記コマンドが実行できれば OK

```powershell
$ uv --version
uv 0.8.22 (ade2bdbd2 2025-09-23)
```
