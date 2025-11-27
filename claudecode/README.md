## ■ .mcp.json を指定して Claude Code を起動する

下記コマンドで「.mcp.json」を指定して Claude Code を起動する

```
claude --mcp-config .mcp.json
```

## ■ 通知音を鳴らすための環境

管理者権限で PowerShell を起動し、下記コマンドで「BurntToast」をインストールする。

```powershell
Install-Module -Name BurntToast -Force
```

下記コマンドを実行し、通知音＋ポップアップが表示されることを確認する。

```powershell
Import-Module BurntToast; New-BurntToastNotification -Text 'ClaudeCode', 'The process is complete' -Sound Default
```

## ■ Claude Code のバージョンアップ

Claude Code の設定ファイル更新

```powershell
$ claude install

✔ Claude Code successfully installed!

  Version: 2.0.55

  Location: C:\Users\ユーザ名\.local\bin\claude.exe
```

Claude Code のバージョンアップ

```powershell
$ claude update
Current version: 2.0.55
Checking for updates...
Claude Code is up to date (2.0.55)
```
