# はじめに

本手順書では Windows11 上への Ollama の導入手順について説明する。

# 1. 公式ページから Ollama をインストールする

[Ollama 公式ページ](https://ollama.com/download/windows)から Windows 版 Ollama をインストールする。

# 2. Ollama で gpt-oss を使ってプロンプトを実行してみる

PowerShell を開き下記コマンドを実行する。※gpt-oss:20b の例

```powershell
$ ollama pull gpt-oss:20b
pulling manifest
pulling b112e727c6f1: 100% ▕██████████████████████████████████████████████████████████▏  13 GB
pulling fa6710a93d78: 100% ▕██████████████████████████████████████████████████████████▏ 7.2 KB
pulling f60356777647: 100% ▕██████████████████████████████████████████████████████████▏  11 KB
pulling d8ba2f9a17b3: 100% ▕██████████████████████████████████████████████████████████▏   18 B
pulling 55c108d8e936: 100% ▕██████████████████████████████████████████████████████████▏  489 B
verifying sha256 digest
writing manifest
success
```

モデルダウンロード後、次のコマンドでプロンプトの実行ができる。

```powershell
$ ollama run gpt-oss:20b
>>> 日本語は話せますか？
Thinking...
User: "日本語は話せますか？" Means: "Can you speak Japanese?" They ask if I can speak Japanese. I need to answer
in Japanese. So respond: "はい、話せます" or more elaborate. Use polite Japanese. Also maybe mention that I can
read/write and understand Japanese. Ok.
...done thinking.

はい、日本語を話すことができます。ご質問やご相談があれば、いつでもどうぞ！

>>> Send a message (/? for help)
```

# その他

## Ollama のプロセス確認

```powershell
$ Get-Process -Name ollama -ErrorAction SilentlyContinue
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    267      20    51992      55004       0.19  30512   1 ollama
```

## Ollama 起動

```powershell
$ ollama serve
```

## Ollama API 一覧

Ollama の主要な API を一覧に示す。（curl コマンドで実行する例）

### モデル一覧取得：GET /api/tags

```
$ curl http://localhost:11434/api/tags

StatusCode        : 200
StatusDescription : OK
Content           : {"models":[{"name":"gpt-oss:120b","model":"gpt-oss:120b","modified_at":"2025-08-21T21:41:11.6099831+09:00","size":65290192093,"digest":"f7f8e2f8f4e087e0e6791636dfe1a28d701d548dada674d12ef0d85ccb02a2a4...
RawContent        : HTTP/1.1 200 OK
                    Content-Length: 675
                    Content-Type: application/json; charset=utf-8
                    Date: Thu, 21 Aug 2025 14:15:56 GMT

                    {"models":[{"name":"gpt-oss:120b","model":"gpt-oss:120b","modified_at":"2025...
Forms             : {}
Headers           : {[Content-Length, 675], [Content-Type, application/json; charset=utf-8], [Date, Thu, 21 Aug 2025 14:15:56 GMT]}
Images            : {}
InputFields       : {}
Links             : {}
ParsedHtml        : System.__ComObject
RawContentLength  : 675

```

### テキスト生成：POST /api/generate

```
$ curl -X POST http://localhost:11434/api/generate \
  -H "Content-Type: application/json" \
  -d '{
        "model": "gpt-oss:20b",
        "prompt": "こんにちは！自己紹介をお願いします。",
        "stream": false
      }'

```

### チャット：POST /api/chat

```
$ curl -X POST http://localhost:11434/api/chat \
  -H "Content-Type: application/json" \
  -d '{
        "model": "gpt-oss:20b",
        "messages": [
          { "role": "system", "content": "You are a helpful assistant." },
          { "role": "user", "content": "日本語で自己紹介してください。" }
        ],
        "stream": false
      }'

```

### セッション確認：GET /api/ps

```
$ curl http://localhost:11434/api/ps
```

### モデルダウンロード：POST /api/pull

```
$ curl -X POST http://localhost:11434/api/pull \
  -H "Content-Type: application/json" \
  -d '{"name": "gpt-oss:20b"}'

```

### モデル削除：DELETE /api/delete

```
curl -X DELETE http://localhost:11434/api/delete \
  -H "Content-Type: application/json" \
  -d '{"name": "gpt-oss:20b"}'

```
