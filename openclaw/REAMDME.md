# はじめに

本手順書では WSL 環境へのOpenClaw 導入手順について説明する。

## ■ 前提

下記を前提とする

- WSLが導入済み
- Node.jsが導入済み

# OpenClawの導入

## ■ npm コマンドでOpenClawをインストールする

下記コマンドでOpenClawをインストールする

```bash
npm install -g openclaw@latest
```

インストール後はパスを通す

```bash
source ~/.bashrc
```

## ■ サービス定義ファイルを事前準備する

[既知不具合](https://github.com/openclaw/openclaw/issues/32635)が原因で後続の手順に失敗する  
そのため、事前にサービス定義ファイルを準備する

サービス定義格納用ディレクトリを作成する

```bash
mkdir -p ~/.config/systemd/user
```

Node.jsとOpenClawのパスを確認しておく  
※NVMで導入したNode.jsの場合

```bash
$ which node
/home/is0383kk/.nvm/versions/node/v24.14.0/bin/node
$ which openclaw
/home/is0383kk/.nvm/versions/node/v24.14.0/bin/openclaw
```

サービス定義ファイル（`~/.config/systemd/user/openclaw-gateway.service`）を作成する

```
[Unit]
Description=OpenClaw Gateway
After=network-online.target
Wants=network-online.target
[Service]
ExecStart=/usr/bin/node /home/is0383kk/.npm-global/bin/openclaw gateway run --port 18789
Restart=always
RestartSec=5
KillMode=process
WorkingDirectory=/home/is0383kk/.openclaw
[Install]
WantedBy=default.target
```

定義ファイルを反映する

```bash
systemctl --user daemon-reload
systemctl --user enable openclaw-gateway.service
systemctl --user start openclaw-gateway.service
```

## ■ OpenClawの初期設定を行う

下記コマンドでOpenClawの初期設定を行う（クイックスタート）  
設定後、TUIでレスポンスが帰ってきたらOK

```bash
openclaw onboard --install-daemon
```

# 各種コマンド

## ■ サービスのステータス確認／起動／停止

OpenClawのステータス確認

```bash
openclaw gateway status
systemctl --user status openclaw-gateway.service
```

OpenClawの起動

```bash
openclaw gateway start
systemctl --user start openclaw-gateway.service
```

OpenClawの停止

```bash
openclaw gateway stop
systemctl --user status openclaw-gateway.service
```

## ■ ダッシュボード画面の起動

TUIでの起動

```bash
openclaw tui
```

ダッシュボード画面の起動

```bash
openclaw dashboard

🦞 OpenClaw 2026.3.2 () — I read logs so you can keep pretending you don't have to.

Dashboard URL: http://127.0.0.1:18789/#token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Copied to clipboard.
No GUI detected. Open from your computer:
ssh -N -L 18789:127.0.0.1:18789 is0383kk@<host>
Then open:
http://localhost:18789/
http://localhost:18789/#token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Docs:
https://docs.openclaw.ai/gateway/remote
https://docs.openclaw.ai/web/control-ui
```

# 参考

- 公式ドキュメント：https://docs.openclaw.ai/ja-JP
