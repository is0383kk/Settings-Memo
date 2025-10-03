# はじめに

本手順書では Windows11 上に uv／uvx をインストールする手順について説明する。

## ■ uv／uvx の導入

下記コマンドで uv／uvx を導入する。

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

その後、下記コマンドでパスを通す。

```bash
export PATH="$HOME/.local/bin:$PATH"
```

下記コマンドが実行できれば OK

```bash
$ uv --version
uv 0.8.22
```
