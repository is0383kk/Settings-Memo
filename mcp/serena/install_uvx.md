# はじめに

本手順書では Windows11 上に Serena を導入するために必要な uv／uvx をインストールする手順について説明する。

## ■ 事前準備：uv／uvx の導入

下記コマンドで uv／uvx を導入する。  
※導入済みの場合はスキップする。

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
$env:Path = "C:\Users\xtuyo\.local\bin;$env:Path"
```

下記コマンドが実行できれば OK

```powershell
$ uv --version
uv 0.8.22 (ade2bdbd2 2025-09-23)
```

## ■ ローカル上で Serena を起動する

下記コマンドで Serena をローカル上で起動する。

```powershell
uvx --from git+https://github.com/oraios/serena serena start-mcp-server --context ide-assistant --project "$(pwd)"
```

正常に起動後、下記リンクにアクセスしローカル起動した Serena のダッシュボードが開ければ OK

- http://127.0.0.1:24282/dashboard/index.html
