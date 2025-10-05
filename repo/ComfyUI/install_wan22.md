# はじめに

本手順書では Windows11 上に ComfyUI × Wan22 環境を構築する手順について説明する  
Wan22 環境を構築することで「テキスト → 動画」や「画像 → 動画」が生成できる

## ■ 前提

下記が導入済みであること

- repo\ComfyUI\install_comfy-ui_win11.md の手順に従い ComfyUI を導入済みであること

### 参考

- https://note.com/seal309midorin/n/n3dc4210b1ff6

# １．Wan22 のサンプルを動かしてみる

## ■ Wan22 の実行に必要なモデルの導入

Wan22 の実行に必要なモデルを導入する

### ① テキストエンコーダ

- 取得先：https://huggingface.co/Comfy-Org/Wan_2.2_ComfyUI_Repackaged/tree/main/split_files/text_encoders
- ファイル名：umt5_xxl_fp8_e4m3fn_scaled.safetensors
- 格納先：ComfyUI/models/text_encoders/

### ②VAE モデル

- 取得先：https://huggingface.co/Comfy-Org/Wan_2.2_ComfyUI_Repackaged/tree/main/split_files/vae
- 取得ファイル名
  - wan_2.1_vae.safetensors
  - wan2.2_vae.safetensors
- 格納先：ComfyUI/models/vae/

### ③diffusion モデル

- 取得先：https://huggingface.co/Comfy-Org/Wan_2.2_ComfyUI_Repackaged/tree/main/split_files/diffusion_models
- 取得ファイル名
  - wan2.2_ti2v_5B_fp16.safetensors
  - wan2.2_t2v_high_noise_14B_fp8_scaled.safetensors
  - wan2.2_i2v_high_noise_14B_fp8_scaled.safetensors
  - wan2.2_i2v_low_noise_14B_fp8_scaled.safetensors
- 格納先：ComfyUI/models/diffusion_models

## ■ ワークフローを構築する

ここではワークフローを構築して Wan22 のサンプルを動かす  
ワークフローのサンプルは下記で提供されている

- 取得先：https://comfyanonymous.github.io/ComfyUI_examples/wan22/
  - repo\ComfyUI\workflow\text2video.json：（テキスト → 画像）
  - repo\ComfyUI\workflow\img2video-h1280w704f72-sample001.json：画像 → 動画（短時間）
  - repo\ComfyUI\workflow\img2video-h1280w704f72-sample002.json：画像 → 動画（長時間）

# ２．おまけ：テキスト → 動画（軽量）

参考：https://note.com/konapieces/n/n65945dcec6c3

- https://www.reddit.com/r/StableDiffusion/comments/1mbuo3o/rtx3060_32_go_ram_wan22_t2v_14b_gguf_512x384_4/

## ■ 実行に必要なモデルの導入

- 取得先：https://huggingface.co/bullerwins/Wan2.2-T2V-A14B-GGUF/tree/main
- ファイル名
  - wan2.2_t2v_high_noise_14B_Q5_K_M.gguf
  - wan2.2_t2v_low_noise_14B_Q5_K_M.gguf
- 格納先：ComfyUI/models/unet

- 取得先：Wan21_T2V_14B_lightx2v_cfg_step_distill_lora_rank32.safetensors
- ファイル名
  - Wan21_T2V_14B_lightx2v_cfg_step_distill_lora_rank32.safetensors
- 格納先：ComfyUI/models/loras/

## ■ ワークフローを構築する

※Manager から「Install Missing Custom Nodes」に移動し「gguf」ノードをインストールしておく

ワークフロー：[video_wan2_2_14B_t2v_RTX3060_v1.json](https://github.com/HerrDehy/SharePublic/blob/main/video_wan2_2_14B_t2v_RTX3060_v1.json)
