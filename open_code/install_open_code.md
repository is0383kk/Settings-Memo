# はじめに

本手順書では Windows11 上への Ollama の導入手順について説明する。

## リリースページから OpenCode のバイナリを取得する

下記ページにアクセスして、Windows 用バイナリ（opencode-windows-x64.zip）をダウンロードする。

- https://github.com/sst/opencode/releases

## ZIP ファイルの解凍＆環境変数の設定

中の exe ファイルを下記に配置＆パスを通す。※手動で「Path」の環境変数に設定してもよい

- C:\Users\<あなた>\.opencode\bin\opencode.exe

```powershell
$ New-Item -ItemType Directory -Force "$HOME\.opencode\bin" | Out-Null
$ setx PATH "$env:PATH;$HOME\.opencode\bin"
```

## OpenCode の動作確認

PowerShell の再起動し、下記コマンド実行しバージョンが表示されれば OK

```powershell
$ opencode --version
0.5.8
```

## OpenCode を試す　※要 Ollama

Ollama が起動していることを確認する。

```powershell
$ Get-Process -Name ollama -ErrorAction SilentlyContinue
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    267      20    51992      55004       0.19  30512   1 ollama
```

OpenCode を実行したいディレクトリに移動し、下記ファイルを配置する。

### opencode.json

```json
{
  "$schema": "https://opencode.ai/config.json",

  "provider": {
    "ollama": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "Ollama (local)",
      "options": {
        "baseURL": "http://localhost:11434/v1"
      },
      "models": {
        "gpt-oss:20b": { "name": "gpt-oss 120B (local)" }
      }
    }
  },

  "model": "ollama/gpt-oss:20b",

  "agent": {
    "build": {
      "description": "Default coding mode with only OpenCode tools.",
      "tools": {
        "read": true,
        "write": true,
        "edit": true,
        "bash": true,
        "grep": true,
        "glob": true,
        "list": true,
        "webfetch": true,
        "patch": true,
        "todoread": true,
        "todowrite": true
      },
      "prompt": "{file:./AGENTS.md}"
    }
  },

  "instructions": ["AGENTS.md"]
}
```

### AGENTS.md

```txt
# Tooling rules for OpenCode
- Use OpenCode tools only: read, write, edit, list, glob, grep, webfetch, bash, task, todowrite, todoread.
- Do NOT call non-existent tools like Repo_browser.\* .
- Prefer `edit` for modifying existing files; use `read` to inspect before editing.
```

## OpenCode を立ち上げる

下記コマンドで立ち上げられる。

```powershell
$ opencode
```
