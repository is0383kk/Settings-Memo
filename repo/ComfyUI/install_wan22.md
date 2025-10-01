# はじめに

本手順書では Windows11 上に ComfyUI × Wan22 環境を構築する手順について説明する。

## ■ 前提

下記が導入済みであること

- repo\ComfyUI\install_comfy-ui_win11.md の手順に従い ComfyUI を導入済みであること

### 参考

- https://note.com/seal309midorin/n/n3dc4210b1ff6

# １．必要なモデルを導入する

Wan22 の実行に必要なモデルを導入していく

## ■ テキストエンコーダ

- 取得先：https://huggingface.co/Comfy-Org/Wan_2.2_ComfyUI_Repackaged/tree/main/split_files/text_encoders
- ファイル名：umt5_xxl_fp8_e4m3fn_scaled.safetensors
- 格納先：ComfyUI/models/text_encoders/

## ■ VAE モデル

- 取得先：https://huggingface.co/Comfy-Org/Wan_2.2_ComfyUI_Repackaged/tree/main/split_files/vae
- 取得ファイル名
  - wan_2.1_vae.safetensors
  - wan2.2_vae.safetensors
- 格納先：ComfyUI/models/vae/

## ■ diffusion モデル

- 取得先：https://huggingface.co/Comfy-Org/Wan_2.2_ComfyUI_Repackaged/tree/main/split_files/diffusion_models
- 取得ファイル名
  - wan2.2_ti2v_5B_fp16.safetensors
  - wan2.2_t2v_high_noise_14B_fp8_scaled.safetensors
  - wan2.2_i2v_high_noise_14B_fp8_scaled.safetensors
  - wan2.2_i2v_low_noise_14B_fp8_scaled.safetensors
- 格納先：ComfyUI/models/diffusion_models

# ２．ワークフローを構築する

ここではワークフローを構築して Wan22 のサンプルを動かす  
ワークフローのサンプルは下記で提供されている

- https://comfyanonymous.github.io/ComfyUI_examples/wan22/

## ■

軽量化：https://note.com/konapieces/n/n65945dcec6c3
