## ■ Claude Code のインストール

Windows の場合、下記コマンドでネイティブインストール可能

```powershell
irm https://claude.ai/install.ps1 | iex
```

下記に exe ファイルがインストールされる
`"C:\Users\ユーザ名\.local\bin\claude.exe"`

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

### バージョンアップ時にエラーが出る場合

インストール時やバージョンアップ時に下記のようなエラーがでる場合

```powershell
$ claude install --force
✘ Installation failed
Could not install - another process is currently installing Claude. Please try again in a moment.
```

```powershell
$ claude update
Current version: 2.0.62
Checking for updates...
Another process is currently updating Claude. Please try again in a moment.
```

下記ディレクトリを削除して再実行すること

- `C:\Users\ユーザ名\.local\state\claude\locks`

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

## ■ transcript ファイル出力先

Claude Code の transcript ファイル出力先
`C:\Users\ユーザ名\.claude\projects\C--Users-ユーザ名-フォルダ名\uuid.jsonl`

```json:transcript.jsonl
{
  "parentUuid": "7f39d02d-7902-46d9-8a11-0f2b2794294b",
  "isSidechain": false,
  "userType": "external",
  "cwd": "C:\\Users\\ユーザ名\\フォルダ名\\フォルダ名\\リポジトリ名",
  "sessionId": "4aab7fda-74e3-45e3-b09f-9146c3ffae8a",
  "version": "2.0.55",
  "gitBranch": "main",
  "message": {
    "model": "claude-sonnet-4-5-20250929",
    "id": "msg_bdrk_XXXXXXXXXXXXXXXXXXX",
    "type": "message",
    "role": "assistant",
    "content": [
      {
        "type": "text",
        "text": "こんにちは！何かお手伝いできることはありますか？\n\nコードの作成、バグの修正、リファクタリング、コードの説明など、ソフトウェア開発に関する様々なタスクをサポートできます。\n\n現在のワーキングディレクトリは `Settings-Memo` というGitリポジトリのようですね。何か作業したいことがあれば教えてください。"
      }
    ],
    "stop_reason": null,
    "stop_sequence": null,
    "usage": {
      "input_tokens": 3,
      "cache_creation_input_tokens": 451,
      "cache_read_input_tokens": 17184,
      "output_tokens": 124
    }
  },
  "type": "assistant",
  "uuid": "f69bcc9c-4e7a-481c-919d-9bd680837dc3",
  "timestamp": "2025-11-29T10:17:36.690Z"
}
```
