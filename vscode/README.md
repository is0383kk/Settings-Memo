# はじめに

本手順書では VSCode の設定手順について説明する。

## ■ 拡張機能リストから拡張機能リストを一括ダウンロード

PowerShell の場合、下記コマンドを実行する

```powershell
$ Get-Content extensions.txt | ForEach-Object { code --install-extension $_ }
```

## ■ VSCode 用の設定ファイルの反映

「ファイル」→「ユーザ設定」→「設定」→「設定（JSON）を開く」  
`settings.json`の内容をコピペする

# 補足：インストール済み拡張機能リストをテキストファイル化

PowerShell を立ち上げる  
下記コマンドでインストール済み拡張機能リストをテキストファイルに出力できる

```powershell
code --list-extensions > extensions.txt
```
