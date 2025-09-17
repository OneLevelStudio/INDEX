# INDEX

Convenience script to start server

## Start server

```
sudo apt update
apt install -y python3.12-venv
docker login
git clone https://github.com/OneLevelStudio/IMAGEN
```

## Server Dashboard

```
sudo snap install ttyd --classic
sudo snap install btop
nohup ttyd -i 0.0.0.0 -p 80 -t disableLeaveAlert=true -t fontSize=20 btop --preset 0 --update 500 &
```

## CDN (HuggingFace alternative)

```
mkdir -p DATA_PUBLIC
wget -O DATA_PUBLIC/W22_I2V_14B_HGH_FP8.safetensors https://huggingface.co/Comfy-Org/Wan_2.2_ComfyUI_Repackaged/resolve/main/split_files/diffusion_models/wan2.2_i2v_high_noise_14B_fp8_scaled.safetensors
wget -O DATA_PUBLIC/W22_I2V_14B_LOW_FP8.safetensors https://huggingface.co/Comfy-Org/Wan_2.2_ComfyUI_Repackaged/resolve/main/split_files/diffusion_models/wan2.2_i2v_low_noise_14B_fp8_scaled.safetensors
wget -O DATA_PUBLIC/UMT5XXL_FP8.safetensors         https://huggingface.co/Comfy-Org/Wan_2.2_ComfyUI_Repackaged/resolve/main/split_files/text_encoders/umt5_xxl_fp8_e4m3fn_scaled.safetensors
wget -O DATA_PUBLIC/W22_I2V_LX2V4S_HGH.safetensors  https://huggingface.co/Comfy-Org/Wan_2.2_ComfyUI_Repackaged/resolve/main/split_files/loras/wan2.2_i2v_lightx2v_4steps_lora_v1_high_noise.safetensors
wget -O DATA_PUBLIC/W22_I2V_LX2V4S_LOW.safetensors  https://huggingface.co/Comfy-Org/Wan_2.2_ComfyUI_Repackaged/resolve/main/split_files/loras/wan2.2_i2v_lightx2v_4steps_lora_v1_low_noise.safetensors
wget -O DATA_PUBLIC/W21_VAE.safetensors             https://huggingface.co/Comfy-Org/Wan_2.2_ComfyUI_Repackaged/resolve/main/split_files/vae/wan_2.1_vae.safetensors

# mkdir -p DATA_PUBLIC
# wget -P DATA_PUBLIC https://huggingface.co/onelevelstudio/VIDGEN/resolve/main/WAN/W22_I2V_14B_HGH_FP8.safetensors
# wget -P DATA_PUBLIC https://huggingface.co/onelevelstudio/VIDGEN/resolve/main/WAN/W22_I2V_14B_LOW_FP8.safetensors
# wget -P DATA_PUBLIC https://huggingface.co/onelevelstudio/VIDGEN/resolve/main/WAN/UMT5XXL_FP8.safetensors
# wget -P DATA_PUBLIC https://huggingface.co/onelevelstudio/VIDGEN/resolve/main/WAN/W22_I2V_LX2V4S_HGH.safetensors
# wget -P DATA_PUBLIC https://huggingface.co/onelevelstudio/VIDGEN/resolve/main/WAN/W22_I2V_LX2V4S_LOW.safetensors
# wget -P DATA_PUBLIC https://huggingface.co/onelevelstudio/VIDGEN/resolve/main/WAN/W21_VAE.safetensors

nohup python3 -m http.server 8000 --directory ./DATA_PUBLIC &
```

## Container: SilverBullet

Data will be saved at: `./DATA_SILVERBULLET`

```
mkdir -p DATA_SILVERBULLET/_plug                                                                                         && \
wget -P DATA_SILVERBULLET https://raw.githubusercontent.com/OneLevelStudio/INDEX/refs/heads/main/CONFIG.md               && \
wget -P DATA_SILVERBULLET/_plug https://raw.githubusercontent.com/OneLevelStudio/INDEX/refs/heads/main/treeview.plug.js  && \
docker run -d \
  --name silverbullet \
  --restart unless-stopped \
  -e SB_HOSTNAME=0.0.0.0 \
  -e SB_USER=admin:admin \
  -p 1234:3000 \
  -v ./DATA_SILVERBULLET:/space \
  ghcr.io/silverbulletmd/silverbullet:v2
```

## Container: Nextcloud

Data will be saved at: `./DATA_NEXTCLOUD/data/<USERNAME>/files`

```
docker run -d \
  --name nextcloud \
  --restart unless-stopped \
  -p 9000:80 \
  -p 9001:443 \
  -v ./DATA_NEXTCLOUD:/var/www/html \
  nextcloud:31.0
```
