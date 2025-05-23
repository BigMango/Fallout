参照 https://blog.csdn.net/strewberry4/article/details/141061188 
基于 cuda124的环境.
千万别安装 cv ,这样会破坏整个cuda的环境,如果错误安装了.
会造成 import torchvision 运行不过

需要设置环境变量 export TORCH_CUDA_ARCH_LIST="8.9"
```
import torch;
print(torch.cuda.get_device_capability())
```

下载 gcc
https://github.com/rcpacini/mingw-w64
https://osdn.net/projects/mingw/downloads/68260/mingw-get-setup.exe/
https://blog.csdn.net/qq_38473254/article/details/136854647?spm=1001.2014.3001.5506

coco的安装不用测试 import cocoapi 可能是版本不同

* 把错误的两个库修改正确
scikit-learn
pillow

* 'torch.six'
  注释本行代码

* Non-existent config key:TENSORBOARD.MODEL_VIS.TOPK
屏蔽SLOWFAST_32x2_R101_50_50.yaml
```
# TENSORBOARD:
#   MODEL_VIS:
#     TOPK: 2
```

* cfg.DEMO.LABEL_FILE_PATH
    https://github.com/facebookresearch/SlowFast/issues/264
    

PIL 下载地址
https://pypi.org/project/pillow/#files
下载
pillow-11.1.0-cp312-cp312-win_amd64.whl 即可


其它参考
[Windows11下安装detectron2超详细教程（免修改版本）（不用进行修改代码）](https://blog.csdn.net/CaiGuoHui1/article/details/129351090)

[SlowFast环境安装爬坑记录](https://www.cxy.red/archives/slowfast-environment-installation-climbing-record-zstcgm)