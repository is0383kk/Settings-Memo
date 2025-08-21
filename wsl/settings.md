# はじめに

本手順書では WSL2 導入後の各種設定について説明する。

## ■ WSL 操作時のベルサウンドをオフにする

WSL 内の 「~/.inputrc」 というファイルに、「set bell-style none」 と書けば、ビープ音を消せる。

```bash
$ echo 'set bell-style none' >> ~/.inputrc
```
