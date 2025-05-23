# 1. Anaconda3

1. 第一步先升级相关的组件
```
sudo apt-get update
sudo apt-get install -y curl
sudo apt-get install -y sudo
sudo apt-get install -y gpg
```
2. 下载conda和安装
```
sudo apt-get install bzip2

清华源 https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/

wget -U NoSuchBrowser/1.0 https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/Anaconda3-5.3.1-Linux-x86_64.sh

sh Anaconda3-5.3.1-MacOSX-x86_64.sh
```

安装Python的时候可以会出现
PackagesNotFoundError
解决方法:
* 增加channel
```
conda config --add channels conda-forge
```
这个方法后期可能会带来一些包查询很慢的问题. 例如 conda search python

```
conda install -c conda-forge
```

# 2. WSL
## 基本命令
查看环境 wsl -l -v
关闭 wsl --shutdown
启动 wsl -d <发行版名称>

## 2.1. 修改安装路径

为了将 WSL 2 的安装位置从 C 盘移动到 D 盘，你可以按照以下步骤操作：

1. 创建目标目录
打开 PowerShell，并运行（以管理员身份运行）以下命令来创建一个目录

```
mkdir D:\WSL\backup
```

2. 确认路径权限
确保你有权限在 D 盘上创建和写入文件。通过尝试在目标路径创建一个测试文件来确认权限：
```
echo "test" > D:\WSL\backup\test.txt
```
3. 导出当前的 WSL 发行版
运行以下命令来导出当前的 Ubuntu 发行版：
```
wsl --export Ubuntu D:\WSL\backup\Ubuntu.tar
```
这会将当前的 Ubuntu 发行版导出为一个 tar 文件。

4. 注销当前的 WSL 发行版
运行以下命令来注销当前的 Ubuntu 发行版：

```
wsl --unregister Ubuntu
```

5. 导入 WSL 发行版到新的位置
运行以下命令将导出的 Ubuntu 发行版导入到 D 盘的新位置：

```
wsl --import Ubuntu D:\WSL\Ubuntu D:\WSL\backup\Ubuntu.tar
```

这会将 Ubuntu 发行版重新安装到 D 盘的 D:\WSL\Ubuntu 目录中。

6. 验证安装
导入完成后，运行以下命令来验证安装是否成功：

```
wsl -l -v
```

你应该会看到类似于之前的输出

7. 启动 WSL
最后，启动 WSL：

```
wsl -d Ubuntu
```

## 2.2. 故障处理
* ERROR_FILE_NOT_FOUND

```cmd
wsl -l
wsl.exe --unregister (版本号)
```

### Label Tools

[Best Open-Source Image Annotation Tools in 2024](https://www.cvat.ai/resources/blog/best-open-source-image-annotation-tools-2024)

+ Computer Vision Annotation Tool (CVAT)
+ LabelMe
+ LabelImg
+ Label Studio (TS)
+ Imagetagger
+ Deeplabel
+ Image annotation comparative table
+ annotation-tool
  
  
https://ecosystem.supervisely.com/apps/nn-image-labeling/annotation-tool

### 2.2.1. 模型工具
* HardLinkShellExt 
  快捷创建各类链接，AI里面的模型视频等占用空间太大，使用这个可以大大的减少硬盘的占用。

* [API Monitor](http://www.rohitab.com/apimonitor)