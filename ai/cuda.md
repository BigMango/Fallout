* cuda tool 版本
  nvcc --version
* NVIDIA 驱动程序版本
  nvidia-smi
* 查看可用python版本
  conda search python

[Windows和WSL安装CUDA](https://blog.csdn.net/Sakuya__/article/details/141254961)

### 正确的环境创建


https://pytorch.org/

现在支持最新的12.8  (2025-04-25)

```
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128
```


pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu124

对于cuda12.x版本，只需要：
XX pip install onnxruntime-gpu==1.19.2

--- pip install pytorch==2.5.1 torchvision==0.20.1 torchaudio==2.5.1 pytorch-cuda==12.4
--- pip install torch==1.11.0+cu113 torchvision==0.12.0+cu113 torchaudio==0.11.0 --extra-index-url https://download.pytorch.org/whl/cu113

[cudda](https://developer.nvidia.com/cudnn-downloads?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exe_local)

[126 找不到库](https://github.com/microsoft/onnxruntime/issues/20049)
主要是path设置错误,需要手动配置path 增加 "C:\Program Files\NVIDIA\CUDNN\v9.8\bin\12.8"

# Linux WSL

## 资源

https://developer.nvidia.com/tensorrt/download/10x

[CUDA Toolkit 12.4 Downloads](https://developer.nvidia.com/cuda-12-8-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=WSL-Ubuntu&target_version=2.0&target_type=deb_local)

[CUDA Toolkit 12.8 Downloads](https://developer.nvidia.com/cuda-12-8-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=WSL-Ubuntu&target_version=2.0&target_type=deb_local)

[Nvidia Tensorrt](https://developer.nvidia.com/tensorrt/download/10x)
[Nvidia Tensorrt Install guide](https://docs.nvidia.com/deeplearning/tensorrt/latest/installing-tensorrt/installing.html)

[TensorRT从安装到推理](https://blog.csdn.net/weixin_52010459/article/details/146565964)

## 疑难杂症

* [Installing CUDA on Ubuntu 23.10 - libt5info not installable](https://askubuntu.com/questions/1491254/installing-cuda-on-ubuntu-23-10-libt5info-not-installable)

1. Open the new file for storing the sources list

```
sudo nano /etc/apt/sources.list.d/ubuntu.sources
```

2. Paste in the following at the end of the file:

```
Types: deb
URIs: http://old-releases.ubuntu.com/ubuntu/
Suites: lunar
Components: universe
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
```

3. Save the file and run sudo apt update - now the install command for CUDA should work.

# 疑难杂症

* AttributeError: module 'distutils._msvccompiler' has no attribute '_get_vc_env'
  除了Sam2以外,其它的项目中只要有 pyproject.toml  文件,pip install -e . 就会出现这个问题
  暂时去掉这个文件

目前Sam 1 有很多其它版本的支持，Sam2 就基本上没有看到了。所以2.0用C#直接开发基本上是没希望了。
