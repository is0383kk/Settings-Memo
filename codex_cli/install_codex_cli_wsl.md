# はじめに

本手順では WSL 環境への Codex CLI の導入手順について説明します。

## ■ Codex のインストール

下記コマンドを使って Codex をインストールします。

```bash
$ npm install -g @openai/codex
added 1 package in 2s
npm notice
npm notice New major version of npm available! 10.9.3 -> 11.5.2
npm notice Changelog: https://github.com/npm/cli/releases/tag/v11.5.2
npm notice To update run: npm install -g npm@11.5.2
npm notice
```

下記コマンドを実行してバージョンが表示されていれば OK です。

```
$ codex --version
codex-cli 0.20.0
```

## ■ Codex CLI のモデルアクセス設定

Codex CLI を使用するためのモデルアクセス設定を行います。
下記の**どちらかで設定する必要があります**。

- Open API キーを使用する
- ChatGPT プランでのログイン

### API キーを所有している場合

Open API キーを所有している場合の設定手順です。

下記コマンドで .bashrc を開き

```bash
$ vi ~/.bashrc
```

下記環境変数で API キーを設定します。

```
export OPENAI_API_KEY="APIキー"
```

設定後は下記コマンドで環境変数を反映させてください。

```bash
source ~/.bashrc
```

### ChatGPT プランでログインする場合

Chat GPT を Plus／Pro プランで契約している場合の設定手順です。

下記コマンドを実行すると、URL リンクが表示されます。

```bash
$ codex login
Starting local login server on http://localhost:1455
. If your browser did not open, navigate to this URL to authenticate:

https://auth.openai.com/oauth/authorize?hogehoge
gio: https://auth.openai.com/oauth/authorize?hogehoge: Operation not supported
```

端末に表示された URL をコピーしてブラウザにペーストすると、ChatGPT の認証画面が開きます。
ユーザ名とパスワードを入力した後、「続行」をクリックします。
認証が成功すると WSL の端末上に **「Successfully logged in」の文字が表示されます**

## ■ Codex CLI の動作確認

Codex CLI の動作確認をしてみます。

任意のディレクトリに移動し、下記コマンドで Codex CLI を起動します。

```bash
$ codex
```

下記のように選択肢が表示されていれば Codex CLI の導入は完了です。

1. Allow Codex to work in this folder without asking for approval
   - 対象フォルダ内で、ユーザの承認なしで Codex による編集・コマンド実行を許可します
2. Require approval of edits and commands
   - 編集やコマンド実行のたびに許可を確認されるようになります

```bash
$ codex
> You are running Codex in /home/is0383kk/React-shadcn-pane-layouts

  Since this folder is version controlled, you may wish to allow Codex
  to work in this folder without asking for approval.

> 1. Yes, allow Codex to work in this folder without asking for approval
  2. No, ask me to approve edits and commands
```
