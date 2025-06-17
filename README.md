# Hunyuan3D-2.1-windows

Windows install for Hunyuan3D-2.1

```sh
git clone https://github.com/Tencent-Hunyuan/Hunyuan3D-2.1
cd Hunyuan3D-2.1
conda create -n Hunyuan3D python=3.11 -y
conda activate Hunyuan3D
conda install cuda -c nvidia/label/cuda-12.4.1 -y
```

- Check nvcc

```sh
nvcc --version
```

- Install libs

```sh
pip install torch==2.5.1 torchvision==0.20.1 torchaudio==2.5.1 --index-url https://download.pytorch.org/whl/cu124
pip install py-cpuinfo
```

- TEMP: Waiting for a compatible release of /deepspeed-0.17.1

```sh
pip install https://files.pythonhosted.org/packages/2e/5c/2058713749655a6b1830ecb8d7db61637a396239610aeb11b59974d29b66/deepspeed-0.15.0-cp311-cp311-win_amd64.whl
```

- Need to bump the bpy version from 4.0 to 4.1 in requirements.txt

```sh
bpy==4.1
```

- Install requirements

```sh
pip install -r requirements.txt
```

## Custom rasterizer

- Copy the content of the custom_rasterizer folder over then run

```sh
cd hy3dpaint/custom_rasterizer
python setup.py install
```

### Known Errors

- link.exe error 1210
From `Visual Studio Install` add `Visual Studio Build Tools 2022`.
Install all tools from "desktop development with c++" and restart powershell.

## Differentiable Renderer

- Copy the content of the differentiable_renderer folder over then run

```sh
cd ../..
cd hy3dpaint/DifferentiableRenderer
python setup.py install
```

## Checkpoints

```sh
cd ../..
mkdir -p hy3dpaint/ckpt
wget https://github.com/xinntao/Real-ESRGAN/releases/download/v0.1.0/RealESRGAN_x4plus.pth -O hy3dpaint/ckpt/RealESRGAN_x4plus.pth
```

## Misc

- Check cuda import

```sh
python -c "import torch; print(torch.version.cuda)"
```

## Remove env

```sh
conda deactivate
conda remove -n Hunyuan3D --all --yes
```
