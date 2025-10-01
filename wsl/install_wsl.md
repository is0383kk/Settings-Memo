# はじめに

本手順書では Windows11 環境への WSL2 の導入手順について説明する。

# １． 事前準備

## ■ Linux カーネルを動かすための互換レイヤーを Windows に追加する

PowerShell を 「管理者として実行」 で立ち上げる。  
下記コマンドを実行する。

```powershell
$ dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

- 機能名: Microsoft-Windows-Subsystem-Linux
- 役割: WSL 自体の機能を Windows にインストール・有効化します。

※ /all は依存関係のある機能もまとめて有効化するオプション。  
※ /norestart は有効化後に自動再起動しない指定

**これが無いと wsl コマンド自体が使えない**とのこと。

## ■ 仮想化基盤を有効化する

下記コマンドを実行する。

```powershell
$ dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

- 機能名: VirtualMachinePlatform
- 役割: 仮想化基盤（Hyper-V の軽量版のようなもの）を有効化する。

※ WSL 2 は軽量な仮想マシン上で Linux カーネルを動かすため、この機能が必須。  
※ これが無いと下記エラーが出る。

```powershell
$ wsl --install
エラー コード: Wsl/InstallDistro/Service/RegisterDistro/CreateVm/HCS/HCS_E_SERVICE_NOT_AVAILABLE
```

## ■ 再起動する

コマンド実行後、再起動する。

# ２. ■ WSL のインストール

下記コマンドで WSL をインストールできる。  
インストール後、パスワードを登録するように促される。

```powershell
$ wsl --install
ダウンロードしています: Ubuntu
インストールしています: Ubuntu
ディストリビューションが正常にインストールされました。'wsl.exe -d Ubuntu' を使用して起動できます
Ubuntu を起動しています...
Provisioning the new WSL instance Ubuntu
This might take a while...
Create a default Unix user account: is0383kk
New password:
Retype new password:
passwd: password updated successfully
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
```

### 【補足】別のディストリビューションを選択する場合

デフォルトでは WSL2 と Ubuntu がインストールされる。  
別のディストリビューションを使う場合は下記のようにオプションで指定できる。

```powershell
wsl --install -d Debian
```

# ３. ■ WSL を使って Ubuntu を起動する

下記コマンドで起動できる。

```powershell
wsl.exe -d Ubuntu
```
