[太方便，WIN系统CUDA12.4下使用conda便捷管理虚拟环境中的不同版本的CUDA、cuDNN、PyTorch-CSDN博客](https://blog.csdn.net/u014451778/article/details/136283099) 

 [太方便，WIN系统CUDA12.4下使用conda便捷管理虚拟环境中的不同版本的CUDA、cuDNN、PyTorch-CSDN博客](https://blog.csdn.net/u014451778/article/details/136283099) 

 [太方便，WIN系统CUDA12.4下使用conda便捷管理虚拟环境中的不同版本的CUDA、cuDNN、PyTorch-CSDN博客](https://blog.csdn.net/u014451778/article/details/136283099) 

 记录工作实践：conda环境中的CUDA、cuDNN与PyTorch的安装与配置
----------------------------------------

#记录工作实践

一、先在系统全局中安装
-----------

查看显卡支持的CUDA版本并安装：

输出：

[NVIDIA-SMI](https://so.csdn.net/so/search?q=NVIDIA-SMI&spm=1001.2101.3001.7020) 551.61                 Driver Version: 551.61         CUDA Version: 12.4  

```
Sun Feb 25 15:29:15 2024
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 551.61                 Driver Version: 551.61         CUDA Version: 12.4     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                     TCC/WDDM  | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  Quadro T2000                 WDDM  |   00000000:01:00.0 Off |                  N/A |
| N/A   57C    P8              3W /   60W |     833MiB /   4096MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
 
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A     44216      C   ...da3\envs\StableDiffusion\python.exe      N/A      |
|    0   N/A  N/A     47780    C+G   C:\Windows\System32\dwm.exe                 N/A      |
+-----------------------------------------------------------------------------------------+
```

可以看到当前显卡和当前驱动程序最高可以支持到**CUDA 12.4** 版本

![](https://i-blog.csdnimg.cn/blog_migrate/9bc8337a69492b826e4df132a4c89151.png)

但是重点来了，CUDA 12.4 Nvidia官方目前还没有更新发布，截止2024年02月25日，Nvidia官方最新的CUDA版本是12.3.2，也就是说，就上图查询出来的驱动和最高支持的版本信息来说，系统全局或是虚拟环境中，只要是安装CUDA12.4及以下版本的CDUA，正常情况下都是可以运行的。

![](https://i-blog.csdnimg.cn/blog_migrate/e6aba21169a87c628144eeb52aa54e49.png)

### `nvidia`官网下载CUDA

下载地址：[CUDA Toolkit Archive | NVIDIA Developer![](https://i-blog.csdnimg.cn/blog_migrate/003a2ce7eb50c2e24a8c624c260c5930.png)
https://developer.nvidia.com/cuda-toolkit-archive](https://developer.nvidia.com/cuda-toolkit-archive "CUDA Toolkit Archive | NVIDIA Developer")

![](https://i-blog.csdnimg.cn/blog_migrate/4abbcf0b4a295c5501e7ea88f7265a7e.png)

### `nvidia`官网下载`cuDNN`

下载地址：[cuDNN Archive | NVIDIA Developer![](https://i-blog.csdnimg.cn/blog_migrate/003a2ce7eb50c2e24a8c624c260c5930.png)
https://developer.nvidia.com/rdp/cudnn-archive](https://developer.nvidia.com/rdp/cudnn-archive "cuDNN Archive | NVIDIA Developer")

保险起见先要在系统全局中安装最新版本的CUDA和cuDNN。

或者，可以同时安装多个版本，例如我的在系统里分别一起安装了：

1、CUDA 12.3版本和对应的cuDNN

这个版本我是为了在虚拟环境中体验最新版本的python3.12及CUDA和cuDNN以及PyTorch安装的

2、CUDA 11.8版本和对应的cuDNN

这个版本是我多数较新的项目能兼容运行的较稳定的版本

![](https://i-blog.csdnimg.cn/blog_migrate/07daf166153d645adeaf71bf541bee3e.png)

设置好环境变量后，可以根据实际情况，通过调整环境变量中“CUDA\_PATH”这一行变量的路径指向来调整优先级，以确认当前系统全局中默认优先使用哪个CUDA版本。调整完后重启（可选）。

![](https://i-blog.csdnimg.cn/blog_migrate/63cfce97c671b558c23c24b3d5edce64.png)

注意了：**虚拟环境中**安装的CUDA版本 不能高于 **系统全局**中最优先的版本。

举个例子，也就是说，假如系统全局变量“CUDA\_PATH”这一行变量中是指向的是CUDA11.8的路径，则conda环境中的cudatoolkit版本号不能高于11.8，即：不能在conda环境中安装CUDA12.1，因为强行安装可以，但不能正常运行，也就是不兼容。

### 系统全局安装CUDA和cuDNN教程（包含验证）：

详细安装方法可以参考本站大神的教程：

包含验证

> [Windows安装cuda和cudnn教程最新版（2023年9月）\_windows更换cudnn-CSDN博客](https://blog.csdn.net/weixin_46530492/article/details/133024073?ops_request_misc=&request_id=&biz_id=102&utm_term=windows11%E5%AE%89%E8%A3%85cuda%E5%92%8Ccundnn&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-133024073.142%5Ev99%5Epc_search_result_base1&spm=1018.2226.3001.4187 "Windows安装cuda和cudnn教程最新版（2023年9月）_windows更换cudnn-CSDN博客")

安装之后也可以用Visual Studio 20XX版本进行验证：

1.  [克隆并导航到https://github.com/NVIDIA/cuda-samples/tree/master/Samples/5\_Domain\_Specific/nbody](https://github.com/NVIDIA/cuda-samples/tree/master/Samples/5_Domain_Specific/nbody "克隆并导航到https://github.com/NVIDIA/cuda-samples/tree/master/Samples/5_Domain_Specific/nbody")`nbody`中的示例目录。
    
2.  打开适用于已安装的 Visual Studio 版本的 nbody Visual Studio 解决方案文件。
    

![](https://i-blog.csdnimg.cn/blog_migrate/fd51534adf0dda8dedd8acce0d14c3aa.png)

3、在 Visual Studio 中打开**“生成”菜单，然后单击****“生成解决方案”**。

![](https://i-blog.csdnimg.cn/blog_migrate/9105272344eb83e5ab800b12b340e9d9.png)

4、导航到 CUDA 示例构建目录并运行 nbody 示例。

**注意**

通过导航到可执行文件的位置来运行示例，否则它将无法找到依赖资源。

![](https://i-blog.csdnimg.cn/blog_migrate/96f1fdbd2c71d820e3c3e4dcb76c1aa4.png)

输出：“GPU设备ID0：“图灵”计算能力7.5”。

```null
GPU Device 0: "Turing" with compute capability 7.5
```

这一方法可参考以下官方文档：

> [CUDA快速入门指南Quick Start Guide 12.3 documentation](https://docs.nvidia.com/cuda/cuda-quick-start-guide/index.html#windows "CUDA快速入门指南Quick Start Guide 12.3 documentation")

### 二、新建conda虚拟环境

新建conda环境，比如拿我新建的这个名为“SDWF”的虚拟环境举例：

（**也可以完全在Anaconda Navigator中进行新建环境--对于管理不同CUDA版本来说是首选推荐选项，因为在手动选择conda渠道中默认稳定的若干可用的python版本中，对从conda渠道安装CUDATOOLKIT工具包来说兼容性最好**）

以管理员身份运行打开“Anaconda Prompt”：

```null
conda create -n SDWF python=3.12.2 -y
```

或者在**Anaconda Navigator中操作**

![](https://i-blog.csdnimg.cn/blog_migrate/563e85b7e7421b90954bb6c6f94fdda1.png)

![](https://i-blog.csdnimg.cn/blog_migrate/f6decae43ca0444ffd35ac2ae49a7407.png)

![](https://i-blog.csdnimg.cn/blog_migrate/75ee9b5015e8c1c8cbf5581964654b9d.png)

用命令新建的，运行完成之后需要进行激活步骤。

### 三、激活虚拟环境

等完成后激活环境：

激活完成后进行安装步骤。

### 四、使用Anaconda Navigator[安装CUDA](https://so.csdn.net/so/search?q=%E5%AE%89%E8%A3%85CUDA&spm=1001.2101.3001.7020)、cuDNN、numpy、PyTorch

然后打开“Anaconda Navigator”，切换到新建的SDWF环境：

![](https://i-blog.csdnimg.cn/blog_migrate/3c8312d6f0fc6b6134eab7a770eabb40.png)

### （一）用Anaconda Navigator安装：

#### **重要：优先建议先安装PyTorch**

**其实可以直接搜项目所需求的PyTorch版本进行安装，conda就会自动匹配进行安装CUDA、cuDNN、numpy了。** 

**如果没有特别的要求，以下搜索结果将会安装最新版本的****PyTorch，当然也可以选择特定的版本进行安装，这将在后续文章内提到。** 

 ![](https://i-blog.csdnimg.cn/blog_migrate/14811c31ffe03518069ea45315c02fd2.png)

等待一小会后可以看到如下窗口：46个包将被安装

![](https://i-blog.csdnimg.cn/blog_migrate/02fb9d4d2b7551378d5e72e104e0f307.png)

 向下滑动窗口将看到conda将自动匹配安装包装CUDA等在内的其他依赖包。

点“Apply”继续。

结束后，打开该环境中的python3.12.2进行验证：

![](https://i-blog.csdnimg.cn/blog_migrate/38c4f86ccf8abf0a74c11c0922c79a67.png)

正常我们应该看到以下界面和输出，详细验证命令请在文中下边小节中找到。

![](https://i-blog.csdnimg.cn/blog_migrate/62756f8af48a8306c00072e5dc26853a.png)

![](https://i-blog.csdnimg.cn/blog_migrate/f54284d27fe77e2c5ac80665c83b175c.png)

#### 如果要分开安装、单独安装CUDA、cuDNN、numpy、PyTorch：

在Anaconda Navigato中打开的新环境中，**如果要分别单独安装**，则：将要显示的内容从左边“installed”（已安装）切换到“Not installed”（未安装），

然后在右上角的输入框中分别输入CUDA、cuDNN、numpy（依赖项）、PyTorch搜索，等待直至显示出搜索结果，安装完再搜索安装下一个：

#### **1、安装CUDA：** 

**输入CUDA后，找到“cuda-toolkit”版本号显示12.3.2的，选中后点击右下角“Apply”安装，点****“Apply”后默认搜寻安装其他依赖项**

**注意：** 

**CUDATOOLKIT工具包，在****12.3****版本是“****cuda-toolkit****”中间有这样****“-”一个****连接符号！！！**

**在****12.3以下的版本是“c****udatoolkit****”！！！中间没有连接符。** 

**比如：** 

**cuda-toolkit 版本 12.3（目前****非常不建议****，各种报错和包冲突，仅供演示说明）**

![](https://i-blog.csdnimg.cn/blog_migrate/59da254c962b7e87f5fa0d1a4579e038.png)

**因为CUDA Python 12.3版本在官方发行说明中指明了此版本有限制 暂不支持CUDA功能！！！！！未来版本中肯定会修复，但是有一些时日。** 

**cudatoolkit 版本 12.1（较新，兼容性比较一般，也****不建议****，因为有些仓库渠道搜不到，仅供演示说明）**

**版本过高会导致一些包不兼容，比如onnxruntime、XFormers库等 项目会依赖到的某些特定的CUDA或PyTorch版本**

**cudatoolkit 版本11.8（比较稳定）**

**cudatoolkit 其它版本 可根据需要自选安装**

![](https://i-blog.csdnimg.cn/blog_migrate/022ca90c404dcf9a0602ee8f3f117ec2.png)

在搜索显示出来的CUDA相关包中，下滑找到“cudatoolkit”选择我们想要安装的版本，比如这里:cuda-toolkit 版本12.3.2

![](https://i-blog.csdnimg.cn/blog_migrate/7b2720e2cdc4655b06121609d3189765.png)

然后点右下角的“Apply”进行安装，后续出现弹窗，一样是继续点“Apply”继续。

#### **2、安装cuDNN：** 

![](https://i-blog.csdnimg.cn/blog_migrate/d976728f8ff3f9c3ac344806f944e00d.png)

![](https://i-blog.csdnimg.cn/blog_migrate/46157503854923f12f09b120621534ab.png)

![](https://i-blog.csdnimg.cn/blog_migrate/455e7acc9459dccb2c7d4d3a7f6fe1d2.png)

#### **3、安装numpy（依赖项）：** 

![](https://i-blog.csdnimg.cn/blog_migrate/f6a993f4eee4c6440c3ae971fcc5c76d.png)

![](https://i-blog.csdnimg.cn/blog_migrate/2c83a5b6d55144a36686ffbc487fe31d.png)

#### **4、安装PyTorch：** 

![](https://i-blog.csdnimg.cn/blog_migrate/7e698040d7d5e82328d946abfa41b325.png)

![](https://i-blog.csdnimg.cn/blog_migrate/11057329b6182488cab5ae8c5abb3eba.png)

![](https://i-blog.csdnimg.cn/blog_migrate/695b8a610ea9f6890b2e2a3c600e184d.png)

另外一个重点来了，截止2024年02月26日，PyTorch官网并未发布支持CUDA12.3的PyTorch版本

![](https://i-blog.csdnimg.cn/blog_migrate/19584462e70c3b02968f60ccadef9524.png)

官网发布的最新支持是到CUDA12.1，还未明确到可以支持CUDA12.3，但是，我们仍然可以用一些命令来在已安装CUDA12.3的电脑上或环境中安装torch以支持张量计算，安装后查询验证时可能会显示为受torch支持的CUDA版本。安装命令有多条可以尝试，请往下查阅。

### （二）用Anaconda Prompt命令安装：

![](https://i-blog.csdnimg.cn/blog_migrate/15bac50278cbc8b99decb4e2e18002d3.png)

#### 1、一条命令安装PyTorch、CUDA、cuDNN

其实：如果对CUDA版本没有特殊的要求的话，在系统全局中已经安装过CUDA12.3.2及以上版本并配置好了环境变量的情况下，**完全可以直接一条命令完成全新的conda的虚拟环境中的CUDA、cuDNN、PyTorch的安装**，原理是基于PyTorch依赖于CUDA和cuDNN，用"conda install"命令先安装PyTorch的话，会默认安装CUDA、cuDNN和其他依赖项。前提是系统中的CUDA版本要高于虚拟环境中的CUDA版本才行。

举个例子：系统全局中安装了CUDA10.0，如果使用这条命令安装，会造成虚拟环境中的CUDA不可用，因为这条命令会简单的在虚拟环境中安装最新的且与虚拟环境兼容的PyTorch和CUDA及cuDNN版本，也就是会安装高于10.0的版本，这会导致无法在虚拟环境中启用CUDA设备。

像我的，我在系统全局中安装了NVIDIA官方最新的CUDA12.3.2，那么conda渠道中的cuda包版本更新肯定是慢于官方版本的，所以用这条命令安装能够成功。反之则不然。

因此，直接安装PyTorch，就会同时匹配安装最新的及兼容的CUDA、cuDNN

用以下命令：

```null
conda install pytorch torchvision torchaudio -c pytorch -c nvidia
```

![](https://i-blog.csdnimg.cn/blog_migrate/24b56baf5051f7900ccaafecea0f8ffc.png)

可以看到将会安装CUDA相关的包

![](https://i-blog.csdnimg.cn/blog_migrate/87e50f0e086343ce2341c7a4978ff4ec.png)

以下是安装完成：

![](https://i-blog.csdnimg.cn/blog_migrate/3de0f5a9516aa53c1eeabdd4c7b99c4b.png)

这是“conda install pytorch torchvision torchaudio -c pytorch -c nvidia”这条命令执行安装结束后，验证的截图：

![](https://i-blog.csdnimg.cn/blog_migrate/4fb776f72fdafccd8f93e018b7384450.png)

可以看到打印出了torch版本“2.2.1”；

打印出了“CUDA 可用： True”；

打印出了“cuDNN 已启用： True”

能计算简单的张量；

打印出使用中的设备是“cuda:0”；

打印出了CUDA可用“CUDA available: True”

打印出了cuDNN已启用“cuDNN enabled: True”

打印出了CUDA的版本号为“12.1”

打印出的cuDNN的版本号为“8801”

因为目前是通过导入torch库进行验证的，而torch库目前支持到的最高CUDA版本是12.1，因此只会打印出“12.1”

虽然conda众多渠道中cuDNN已更新到8.9版本，但是为了与当前环境兼容，或许conda认为cuDNN8.8.0.1才是当前虚拟环境的最优选择。

#### 2、也可以用单独的指定包的安装命令进行安装：

##### （1）安装CUDA和cuDNN

###### a）安装12.3版本

conda install cuda-toolkit=12.3 cuDNN

```null
conda install cuda-toolkit=12.3 cuDNN
```

######  b）安装12.1版本

conda install cudatoolkit=12.1 cuDNN

```null
conda install cudatoolkit=12.1 cuDNN
```

###### c）安装11.8版本

conda install cudatoolkit=11.8 cuDNN

```null
conda install cudatoolkit=11.8 cuDNN
```

###### d）以此类推。

其他版本以此类推。

##### （2）安装numpy（依赖项）(可选)

conda install numpy

在某些较高或较低CUDA版本安装时，如果没有默认安装此依赖，则需要单独进行此项安装，如果已经安装了，则不用重复安装。举例说明，如果验证或使用中报错“No module named NumPy”，则需要进行这项安装。也可以用pip命令，但是如大家所知，冲突需要额外解决。

##### （3）安装PyTorch 

仅限Nvidia (英伟达)支持CUDA12.X版本用户：

###### a）conda命令安装：

（用conda命令进行安装无需进行过多的手动依赖处理）

conda install pytorch torchvision torchaudio -c pytorch -c nvidia

```null
conda install pytorch torchvision torchaudio -c pytorch -c nvidia
```

这个命令将使用 PyTorch 的最新稳定版本进行安装。

如果不行，则可以尝试这两条命令：

```null
conda install pytorch==2.1.0 torchvision==0.16.0 torchaudio==2.1.0 pytorch-cuda=12.1 -c pytorch -c nvidia
```

```null
conda install pytorch==2.1.2 torchvision==0.16.2 torchaudio==2.1.2 pytorch-cuda=12.1 -c pytorch -c nvidia
```

这两条命令是指定安装较旧或较新版本的PyTorch来尝试使程序能够正常运行。

另外版本号可以自行修改，修改成项目需求的版本，比如“pytorch==2.2.0”

```null
conda install pytorch==2.2.0 torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia
```

这条命令仅指定了pytorch==2.2.0，pytorch-cuda=12.1，但是torchvision和torchaudio的版本没有指定，这样编写命令的作用是conda会在安装指定版的包 的同时，对torchvision和torchaudio进行匹配安装以确保最大限度的兼容。

可用于更换PyTorch版本的conda虚拟环境（举个例子：比如stable diffusion webui 需要用到XFormers库，但我安装了CUDA12.1对应的pytorch==2.2.1版，而安装XFormers后自动重装Torch版本到2.2.0了，但是torchvision和torchaudio却没有重新安装，导致同样不兼容无法正常运行，鉴于这种情况，可用上边这条命令进行重装，使各运行库之间最大限度匹配兼容和保证正确安装）。

###### b）pip命令安装：

（用pip命令进行安装可能需要额外手动进行依赖或冲突的安装升降级处理）

还可以使用以下**pip**命令在环境Anaconda Prompt中安装稳定的 CUDA12.1版本PyTorch：

pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu121

```null
pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu121
```

还有，这是每晚安装 PyTorch 的命令，它是一个支持python 3.12 的包，可能会有性能改进：

pip install --pre torch torchvision torchaudio --index-url https://download.pytorch.org/whl/nightly/cu121

```null
pip install --pre torch torchvision torchaudio --index-url https://download.pytorch.org/whl/nightly/cu121
```

###### c）更多安装命令:

请参阅PyTorch官网：

> [Start Locally | PyTorch](https://pytorch.org/get-started/locally/ "Start Locally | PyTorch")

#### 3、查询conda中可用版本的命令:

与查寻可用软件包版本的用法一样：conda search <包名>

##### a）查询可用的CUDA版本

conda search cuda

输出信息界面如下，从低版本到高版本的排列，最新的在最下边：

```null
(base) C:\Windows\System32>conda search cudacuda                          11.3.0      hd997d6f_0  nvidiacuda                          11.4.0      h15006a4_0  nvidiacuda                          11.4.1      ha196465_0  nvidiacuda                          11.4.2      hffd2907_0  nvidiacuda                          11.4.3      h88d1909_0  nvidiacuda                          11.4.4      h5680c20_0  nvidiacuda                          11.5.0      h1d80479_0  nvidiacuda                          11.5.1      h94c0a3e_0  nvidiacuda                          11.5.2      h64e5439_0  nvidiacuda                          11.6.0      h15814fa_0  nvidiacuda                          11.6.1      h0216371_0  nvidiacuda                          11.6.2      h65bbf44_0  nvidiacuda                          12.0.0      h7428d3b_0  anaconda/cloud/conda-forgecuda                          12.0.0      h7428d3b_0  conda-forgecuda                          12.0.0      h7428d3b_1  anaconda/cloud/conda-forgecuda                          12.0.0      h7428d3b_1  conda-forgecuda                          12.0.0      ha804496_0  anaconda/cloud/conda-forgecuda                          12.0.0      ha804496_0  conda-forgecuda                          12.0.0      ha804496_1  anaconda/cloud/conda-forgecuda                          12.0.0      ha804496_1  conda-forgecuda                          12.1.1      h7428d3b_0  anaconda/cloud/conda-forgecuda                          12.1.1      h7428d3b_0  conda-forgecuda                          12.1.1      ha804496_0  anaconda/cloud/conda-forgecuda                          12.1.1      ha804496_0  conda-forgecuda                          12.2.2      h7428d3b_0  anaconda/cloud/conda-forgecuda                          12.2.2      h7428d3b_0  conda-forgecuda                          12.2.2      ha804496_0  anaconda/cloud/conda-forgecuda                          12.2.2      ha804496_0  conda-forgecuda                          12.3.2      h7428d3b_0  anaconda/cloud/conda-forgecuda                          12.3.2      h7428d3b_0  conda-forgecuda                          12.3.2      ha804496_0  anaconda/cloud/conda-forgecuda                          12.3.2      ha804496_0  conda-forge
```

##### b）查询可用的cudatoolkit版本

conda search cudatoolkit

###### 或者

```null
conda search cuda-toolkit
```

输出信息界面如下，从低版本到高版本的排列，最新的在最下边：

```null
(base) C:\Windows\System32>conda search cudatoolkitcudatoolkit                      8.0               4  pkgs/maincudatoolkit                      9.0               1  pkgs/maincudatoolkit                      9.2               0  pkgs/maincudatoolkit                  9.2.148     h08c830c_10  anaconda/cloud/conda-forgecudatoolkit                  9.2.148     h08c830c_10  conda-forgecudatoolkit                  9.2.148      h08c830c_6  anaconda/cloud/conda-forgecudatoolkit                  9.2.148      h08c830c_6  conda-forgecudatoolkit                  9.2.148      h08c830c_7  anaconda/cloud/conda-forgecudatoolkit                  9.2.148      h08c830c_7  conda-forgecudatoolkit                  9.2.148      h08c830c_8  anaconda/cloud/conda-forgecudatoolkit                  9.2.148      h08c830c_8  conda-forgecudatoolkit                  9.2.148      h08c830c_9  anaconda/cloud/conda-forgecudatoolkit                  9.2.148      h08c830c_9  conda-forgecudatoolkit                  9.2.148     h9c7d20e_10  anaconda/cloud/conda-forgecudatoolkit                  9.2.148     h9c7d20e_10  conda-forgecudatoolkit                  9.2.148     h9c7d20e_11  anaconda/cloud/conda-forgecudatoolkit                  9.2.148     h9c7d20e_11  conda-forgecudatoolkit                  9.2.148     h9c7d20e_12  anaconda/cloud/conda-forgecudatoolkit                  9.2.148     h9c7d20e_12  conda-forgecudatoolkit                  9.2.148     h9c7d20e_13  anaconda/cloud/conda-forgecudatoolkit                  9.2.148     h9c7d20e_13  conda-forgecudatoolkit                 10.0.130               0  pkgs/maincudatoolkit                 10.0.130     h5327add_10  anaconda/cloud/conda-forgecudatoolkit                 10.0.130     h5327add_10  conda-forgecudatoolkit                 10.0.130      h5327add_6  anaconda/cloud/conda-forgecudatoolkit                 10.0.130      h5327add_6  conda-forgecudatoolkit                 10.0.130      h5327add_7  anaconda/cloud/conda-forgecudatoolkit                 10.0.130      h5327add_7  conda-forgecudatoolkit                 10.0.130      h5327add_8  anaconda/cloud/conda-forgecudatoolkit                 10.0.130      h5327add_8  conda-forgecudatoolkit                 10.0.130      h5327add_9  anaconda/cloud/conda-forgecudatoolkit                 10.0.130      h5327add_9  conda-forgecudatoolkit                 10.0.130     he4282a3_10  anaconda/cloud/conda-forgecudatoolkit                 10.0.130     he4282a3_10  conda-forgecudatoolkit                 10.0.130     he4282a3_11  anaconda/cloud/conda-forgecudatoolkit                 10.0.130     he4282a3_11  conda-forgecudatoolkit                 10.0.130     he4282a3_12  anaconda/cloud/conda-forgecudatoolkit                 10.0.130     he4282a3_12  conda-forgecudatoolkit                 10.0.130     he4282a3_13  anaconda/cloud/conda-forgecudatoolkit                 10.0.130     he4282a3_13  conda-forgecudatoolkit                 10.1.168               0  pkgs/maincudatoolkit                 10.1.243     h3826478_10  anaconda/cloud/conda-forgecudatoolkit                 10.1.243     h3826478_10  conda-forgecudatoolkit                 10.1.243      h3826478_6  anaconda/cloud/conda-forgecudatoolkit                 10.1.243      h3826478_6  conda-forgecudatoolkit                 10.1.243      h3826478_7  anaconda/cloud/conda-forgecudatoolkit                 10.1.243      h3826478_7  conda-forgecudatoolkit                 10.1.243      h3826478_8  anaconda/cloud/conda-forgecudatoolkit                 10.1.243      h3826478_8  conda-forgecudatoolkit                 10.1.243      h3826478_9  anaconda/cloud/conda-forgecudatoolkit                 10.1.243      h3826478_9  conda-forgecudatoolkit                 10.1.243      h74a9793_0  pkgs/maincudatoolkit                 10.1.243     hc75346c_10  anaconda/cloud/conda-forgecudatoolkit                 10.1.243     hc75346c_10  conda-forgecudatoolkit                 10.1.243     hc75346c_11  anaconda/cloud/conda-forgecudatoolkit                 10.1.243     hc75346c_11  conda-forgecudatoolkit                 10.1.243     hc75346c_12  anaconda/cloud/conda-forgecudatoolkit                 10.1.243     hc75346c_12  conda-forgecudatoolkit                 10.1.243     hc75346c_13  anaconda/cloud/conda-forgecudatoolkit                 10.1.243     hc75346c_13  conda-forgecudatoolkit                  10.2.89      h74a9793_0  pkgs/maincudatoolkit                  10.2.89      h74a9793_1  pkgs/maincudatoolkit                  10.2.89     hb195166_10  anaconda/cloud/conda-forgecudatoolkit                  10.2.89     hb195166_10  conda-forgecudatoolkit                  10.2.89      hb195166_6  anaconda/cloud/conda-forgecudatoolkit                  10.2.89      hb195166_6  conda-forgecudatoolkit                  10.2.89      hb195166_7  anaconda/cloud/conda-forgecudatoolkit                  10.2.89      hb195166_7  conda-forgecudatoolkit                  10.2.89      hb195166_8  anaconda/cloud/conda-forgecudatoolkit                  10.2.89      hb195166_8  conda-forgecudatoolkit                  10.2.89      hb195166_9  anaconda/cloud/conda-forgecudatoolkit                  10.2.89      hb195166_9  conda-forgecudatoolkit                  10.2.89     he40447d_10  anaconda/cloud/conda-forgecudatoolkit                  10.2.89     he40447d_10  conda-forgecudatoolkit                  10.2.89     he40447d_11  anaconda/cloud/conda-forgecudatoolkit                  10.2.89     he40447d_11  conda-forgecudatoolkit                  10.2.89     he40447d_12  anaconda/cloud/conda-forgecudatoolkit                  10.2.89     he40447d_12  conda-forgecudatoolkit                  10.2.89     he40447d_13  anaconda/cloud/conda-forgecudatoolkit                  10.2.89     he40447d_13  conda-forgecudatoolkit                   11.0.3     h3f58a73_10  anaconda/cloud/conda-forgecudatoolkit                   11.0.3     h3f58a73_10  conda-forgecudatoolkit                   11.0.3      h3f58a73_6  anaconda/cloud/conda-forgecudatoolkit                   11.0.3      h3f58a73_6  conda-forgecudatoolkit                   11.0.3      h3f58a73_7  anaconda/cloud/conda-forgecudatoolkit                   11.0.3      h3f58a73_7  conda-forgecudatoolkit                   11.0.3      h3f58a73_8  anaconda/cloud/conda-forgecudatoolkit                   11.0.3      h3f58a73_8  conda-forgecudatoolkit                   11.0.3      h3f58a73_9  anaconda/cloud/conda-forgecudatoolkit                   11.0.3      h3f58a73_9  conda-forgecudatoolkit                   11.0.3     hd336c7a_10  anaconda/cloud/conda-forgecudatoolkit                   11.0.3     hd336c7a_10  conda-forgecudatoolkit                   11.0.3     hd336c7a_11  anaconda/cloud/conda-forgecudatoolkit                   11.0.3     hd336c7a_11  conda-forgecudatoolkit                   11.0.3     hd336c7a_12  anaconda/cloud/conda-forgecudatoolkit                   11.0.3     hd336c7a_12  conda-forgecudatoolkit                   11.0.3     hd336c7a_13  anaconda/cloud/conda-forgecudatoolkit                   11.0.3     hd336c7a_13  conda-forgecudatoolkit                 11.0.221      h74a9793_0  pkgs/maincudatoolkit                   11.1.1     hb074779_10  anaconda/cloud/conda-forgecudatoolkit                   11.1.1     hb074779_10  conda-forgecudatoolkit                   11.1.1     hb074779_11  anaconda/cloud/conda-forgecudatoolkit                   11.1.1     hb074779_11  conda-forgecudatoolkit                   11.1.1     hb074779_12  anaconda/cloud/conda-forgecudatoolkit                   11.1.1     hb074779_12  conda-forgecudatoolkit                   11.1.1     hb074779_13  anaconda/cloud/conda-forgecudatoolkit                   11.1.1     hb074779_13  conda-forgecudatoolkit                   11.1.1     heb2d755_10  anaconda/cloud/conda-forgecudatoolkit                   11.1.1     heb2d755_10  conda-forgecudatoolkit                   11.1.1      heb2d755_6  anaconda/cloud/conda-forgecudatoolkit                   11.1.1      heb2d755_6  conda-forgecudatoolkit                   11.1.1      heb2d755_7  anaconda/cloud/conda-forgecudatoolkit                   11.1.1      heb2d755_7  conda-forgecudatoolkit                   11.1.1      heb2d755_9  anaconda/cloud/conda-forgecudatoolkit                   11.1.1      heb2d755_9  conda-forgecudatoolkit                   11.2.0      h608a323_7  anaconda/cloud/conda-forgecudatoolkit                   11.2.0      h608a323_7  conda-forgecudatoolkit                   11.2.0      h608a323_8  anaconda/cloud/conda-forgecudatoolkit                   11.2.0      h608a323_8  conda-forgecudatoolkit                   11.2.1      h7a7aa70_8  anaconda/cloud/conda-forgecudatoolkit                   11.2.1      h7a7aa70_8  conda-forgecudatoolkit                   11.2.2     h7d7167e_10  anaconda/cloud/conda-forgecudatoolkit                   11.2.2     h7d7167e_10  conda-forgecudatoolkit                   11.2.2     h7d7167e_11  anaconda/cloud/conda-forgecudatoolkit                   11.2.2     h7d7167e_11  conda-forgecudatoolkit                   11.2.2     h7d7167e_12  anaconda/cloud/conda-forgecudatoolkit                   11.2.2     h7d7167e_12  conda-forgecudatoolkit                   11.2.2     h7d7167e_13  anaconda/cloud/conda-forgecudatoolkit                   11.2.2     h7d7167e_13  conda-forgecudatoolkit                   11.2.2     h933977f_10  anaconda/cloud/conda-forgecudatoolkit                   11.2.2     h933977f_10  conda-forgecudatoolkit                   11.2.2      h933977f_8  anaconda/cloud/conda-forgecudatoolkit                   11.2.2      h933977f_8  conda-forgecudatoolkit                   11.2.2      h933977f_9  anaconda/cloud/conda-forgecudatoolkit                   11.2.2      h933977f_9  conda-forgecudatoolkit                   11.3.1     h280eb24_10  anaconda/cloud/conda-forgecudatoolkit                   11.3.1     h280eb24_10  conda-forgecudatoolkit                   11.3.1      h280eb24_9  anaconda/cloud/conda-forgecudatoolkit                   11.3.1      h280eb24_9  conda-forgecudatoolkit                   11.3.1      h59b6b97_2  pkgs/maincudatoolkit                   11.3.1     hf2f0253_10  anaconda/cloud/conda-forgecudatoolkit                   11.3.1     hf2f0253_10  conda-forgecudatoolkit                   11.3.1     hf2f0253_11  anaconda/cloud/conda-forgecudatoolkit                   11.3.1     hf2f0253_11  conda-forgecudatoolkit                   11.3.1     hf2f0253_12  anaconda/cloud/conda-forgecudatoolkit                   11.3.1     hf2f0253_12  conda-forgecudatoolkit                   11.3.1     hf2f0253_13  anaconda/cloud/conda-forgecudatoolkit                   11.3.1     hf2f0253_13  conda-forgecudatoolkit                   11.4.2     h0e0bcb6_10  anaconda/cloud/conda-forgecudatoolkit                   11.4.2     h0e0bcb6_10  conda-forgecudatoolkit                   11.4.2      h0e0bcb6_9  anaconda/cloud/conda-forgecudatoolkit                   11.4.2      h0e0bcb6_9  conda-forgecudatoolkit                   11.4.2     h4738e3e_10  anaconda/cloud/conda-forgecudatoolkit                   11.4.2     h4738e3e_10  conda-forgecudatoolkit                   11.4.2     h4738e3e_11  anaconda/cloud/conda-forgecudatoolkit                   11.4.2     h4738e3e_11  conda-forgecudatoolkit                   11.4.3     h208a305_12  anaconda/cloud/conda-forgecudatoolkit                   11.4.3     h208a305_12  conda-forgecudatoolkit                   11.4.3     h208a305_13  anaconda/cloud/conda-forgecudatoolkit                   11.4.3     h208a305_13  conda-forgecudatoolkit                   11.5.0      hfde6d1b_9  anaconda/cloud/conda-forgecudatoolkit                   11.5.0      hfde6d1b_9  conda-forgecudatoolkit                   11.5.0      hfde6d1b_9  nvidiacudatoolkit                   11.5.1     hac7d16d_10  anaconda/cloud/conda-forgecudatoolkit                   11.5.1     hac7d16d_10  conda-forgecudatoolkit                   11.5.1      hac7d16d_9  anaconda/cloud/conda-forgecudatoolkit                   11.5.1      hac7d16d_9  conda-forgecudatoolkit                   11.5.1     hacd90e7_10  anaconda/cloud/conda-forgecudatoolkit                   11.5.1     hacd90e7_10  conda-forgecudatoolkit                   11.5.1     hacd90e7_11  anaconda/cloud/conda-forgecudatoolkit                   11.5.1     hacd90e7_11  conda-forgecudatoolkit                   11.5.2     h7b70026_12  anaconda/cloud/conda-forgecudatoolkit                   11.5.2     h7b70026_12  conda-forgecudatoolkit                   11.5.2     h7b70026_13  anaconda/cloud/conda-forgecudatoolkit                   11.5.2     h7b70026_13  conda-forgecudatoolkit                   11.6.0     h5c2934b_10  anaconda/cloud/conda-forgecudatoolkit                   11.6.0     h5c2934b_10  conda-forgecudatoolkit                   11.6.0     h5c2934b_11  anaconda/cloud/conda-forgecudatoolkit                   11.6.0     h5c2934b_11  conda-forgecudatoolkit                   11.6.0     hc0ea762_10  anaconda/cloud/conda-forgecudatoolkit                   11.6.0     hc0ea762_10  conda-forgecudatoolkit                   11.6.0      hc0ea762_9  anaconda/cloud/conda-forgecudatoolkit                   11.6.0      hc0ea762_9  conda-forgecudatoolkit                   11.6.1     h4c184bc_12  anaconda/cloud/conda-forgecudatoolkit                   11.6.1     h4c184bc_12  conda-forgecudatoolkit                   11.6.1     h4c184bc_13  anaconda/cloud/conda-forgecudatoolkit                   11.6.1     h4c184bc_13  conda-forgecudatoolkit                   11.6.2     h3aee862_12  anaconda/cloud/conda-forgecudatoolkit                   11.6.2     h3aee862_12  conda-forgecudatoolkit                   11.6.2     h3aee862_13  anaconda/cloud/conda-forgecudatoolkit                   11.6.2     h3aee862_13  conda-forgecudatoolkit                   11.7.0     h74894db_10  anaconda/cloud/conda-forgecudatoolkit                   11.7.0     h74894db_10  conda-forgecudatoolkit                   11.7.0     h74894db_11  anaconda/cloud/conda-forgecudatoolkit                   11.7.0     h74894db_11  conda-forgecudatoolkit                   11.7.0     ha6f8bbd_10  anaconda/cloud/conda-forgecudatoolkit                   11.7.0     ha6f8bbd_10  conda-forgecudatoolkit                   11.7.1     haa0b59a_12  anaconda/cloud/conda-forgecudatoolkit                   11.7.1     haa0b59a_12  conda-forgecudatoolkit                   11.7.1     haa0b59a_13  anaconda/cloud/conda-forgecudatoolkit                   11.7.1     haa0b59a_13  conda-forgecudatoolkit                   11.8.0     h09e9e62_10  anaconda/cloud/conda-forgecudatoolkit                   11.8.0     h09e9e62_10  conda-forgecudatoolkit                   11.8.0     h09e9e62_11  anaconda/cloud/conda-forgecudatoolkit                   11.8.0     h09e9e62_11  conda-forgecudatoolkit                   11.8.0     h09e9e62_12  anaconda/cloud/conda-forgecudatoolkit                   11.8.0     h09e9e62_12  conda-forgecudatoolkit                   11.8.0     h09e9e62_13  anaconda/cloud/conda-forgecudatoolkit                   11.8.0     h09e9e62_13  conda-forgecudatoolkit                   11.8.0      hd77b12b_0  pkgs/main
```

##### c）查询可用的cuDNN版本

conda search cudnn

输出信息界面如下，从低版本到高版本的排列，最新的在最下边：

```null
(base) C:\Windows\System32>conda search cudnncudnn                          7.1.4       cuda8.0_0  pkgs/maincudnn                          7.1.4       cuda9.0_0  pkgs/maincudnn                          7.3.1      cuda10.0_0  pkgs/maincudnn                          7.3.1       cuda9.0_0  pkgs/maincudnn                          7.6.0      cuda10.0_0  pkgs/maincudnn                          7.6.0      cuda10.1_0  pkgs/maincudnn                          7.6.0       cuda9.0_0  pkgs/maincudnn                          7.6.4      cuda10.0_0  pkgs/maincudnn                          7.6.4      cuda10.1_0  pkgs/maincudnn                          7.6.4       cuda9.0_0  pkgs/maincudnn                          7.6.5      cuda10.0_0  pkgs/maincudnn                          7.6.5      cuda10.1_0  pkgs/maincudnn                          7.6.5      cuda10.2_0  pkgs/maincudnn                          7.6.5       cuda9.0_0  pkgs/maincudnn                          7.6.5       cuda9.2_0  pkgs/maincudnn                       7.6.5.32      h2cb8ba8_1  anaconda/cloud/conda-forgecudnn                       7.6.5.32      h2cb8ba8_1  conda-forgecudnn                       7.6.5.32      h36d860d_1  anaconda/cloud/conda-forgecudnn                       7.6.5.32      h36d860d_1  conda-forgecudnn                       7.6.5.32      h37a4af2_1  anaconda/cloud/conda-forgecudnn                       7.6.5.32      h37a4af2_1  conda-forgecudnn                       8.0.5.39      h36d860d_1  anaconda/cloud/conda-forgecudnn                       8.0.5.39      h36d860d_1  conda-forgecudnn                       8.0.5.39      h37a4af2_1  anaconda/cloud/conda-forgecudnn                       8.0.5.39      h37a4af2_1  conda-forgecudnn                       8.0.5.39      hfe7f257_1  anaconda/cloud/conda-forgecudnn                       8.0.5.39      hfe7f257_1  conda-forgecudnn                       8.1.0.77      h37a4af2_0  anaconda/cloud/conda-forgecudnn                       8.1.0.77      h37a4af2_0  conda-forgecudnn                       8.1.0.77      h3e0f4f4_0  anaconda/cloud/conda-forgecudnn                       8.1.0.77      h3e0f4f4_0  conda-forgecudnn                       8.2.0.53      h754d62a_0  anaconda/cloud/conda-forgecudnn                       8.2.0.53      h754d62a_0  conda-forgecudnn                       8.2.0.53      hae0fe6e_0  anaconda/cloud/conda-forgecudnn                       8.2.0.53      hae0fe6e_0  conda-forgecudnn                          8.2.1      cuda11.3_0  pkgs/maincudnn                       8.2.1.32      h754d62a_0  anaconda/cloud/conda-forgecudnn                       8.2.1.32      h754d62a_0  conda-forgecudnn                       8.2.1.32      hae0fe6e_0  anaconda/cloud/conda-forgecudnn                       8.2.1.32      hae0fe6e_0  conda-forgecudnn                       8.3.2.44      hf5f08ae_0  anaconda/cloud/conda-forgecudnn                       8.3.2.44      hf5f08ae_0  conda-forgecudnn                       8.3.2.44      hf5f08ae_1  anaconda/cloud/conda-forgecudnn                       8.3.2.44      hf5f08ae_1  conda-forgecudnn                       8.4.0.27      hf5f08ae_0  anaconda/cloud/conda-forgecudnn                       8.4.0.27      hf5f08ae_0  conda-forgecudnn                       8.4.0.27      hf5f08ae_1  anaconda/cloud/conda-forgecudnn                       8.4.0.27      hf5f08ae_1  conda-forgecudnn                       8.4.1.50      hf5f08ae_0  anaconda/cloud/conda-forgecudnn                       8.4.1.50      hf5f08ae_0  conda-forgecudnn                      8.8.0.121      h84bb9a4_3  anaconda/cloud/conda-forgecudnn                      8.8.0.121      h84bb9a4_3  conda-forgecudnn                      8.8.0.121      h84bb9a4_4  anaconda/cloud/conda-forgecudnn                      8.8.0.121      h84bb9a4_4  conda-forgecudnn                      8.8.0.121      h84bb9a4_5  anaconda/cloud/conda-forgecudnn                      8.8.0.121      h84bb9a4_5  conda-forgecudnn                      8.8.0.121      h9631440_0  anaconda/cloud/conda-forgecudnn                      8.8.0.121      h9631440_0  conda-forgecudnn                      8.8.0.121      h9631440_1  anaconda/cloud/conda-forgecudnn                      8.8.0.121      h9631440_1  conda-forgecudnn                      8.8.0.121      h9631440_2  anaconda/cloud/conda-forgecudnn                      8.8.0.121      h9631440_2  conda-forgecudnn                      8.8.0.121      h9631440_3  anaconda/cloud/conda-forgecudnn                      8.8.0.121      h9631440_3  conda-forgecudnn                      8.8.0.121      h9631440_4  anaconda/cloud/conda-forgecudnn                      8.8.0.121      h9631440_4  conda-forgecudnn                      8.8.0.121      hc5a83b5_5  anaconda/cloud/conda-forgecudnn                      8.8.0.121      hc5a83b5_5  conda-forgecudnn                      8.8.0.121      hc794521_4  anaconda/cloud/conda-forgecudnn                      8.8.0.121      hc794521_4  conda-forgecudnn                       8.9.1.23      h84bb9a4_0  anaconda/cloud/conda-forgecudnn                       8.9.1.23      h84bb9a4_0  conda-forgecudnn                       8.9.1.23      hc5a83b5_0  anaconda/cloud/conda-forgecudnn                       8.9.1.23      hc5a83b5_0  conda-forgecudnn                       8.9.2.26        cuda11_0  pkgs/maincudnn                       8.9.7.29      h84bb9a4_0  anaconda/cloud/conda-forgecudnn                       8.9.7.29      h84bb9a4_0  conda-forgecudnn                       8.9.7.29      h84bb9a4_1  anaconda/cloud/conda-forgecudnn                       8.9.7.29      h84bb9a4_1  conda-forgecudnn                       8.9.7.29      hc5a83b5_0  anaconda/cloud/conda-forgecudnn                       8.9.7.29      hc5a83b5_0  conda-forgecudnn                       8.9.7.29      hc5a83b5_1  anaconda/cloud/conda-forgecudnn                       8.9.7.29      hc5a83b5_1  conda-forge
```

##### d）简化的安装命令:

查询结束之后，想单独安装某一版本的CUDA和cuDNN则可使用以下简化命令：

```null
conda install cudatoolkit=11.8 cuDNN
```

这将在当前环境中安装cudatoolkit=11.8工具包和兼容的cuDNN。

```null
​conda install cudatoolkit=12.1 cuDNN
```

这将在当前环境中安装cudatoolkit=12.1工具包和兼容的cuDNN。

```null
​conda install cudatoolkit -c nvidiaconda install cudnn -c nvidia
```

这两条命令执行完后，将从指定的nvidia渠道获取并在当前环境中安装兼容环境的cudatoolkit工具包和兼容的cuDNN。

或者，也可以尝试以下安装命令：

主打一个疯狂尝试，说不定有效呢

### **从 PyPI 安装**

```
pip install cuda-python 
```

```null
pip install cuda-python
```

### **从 Conda 安装[#](https://nvidia.github.io/cuda-python/install.html#installing-from-conda "#")**

```
conda install -c nvidia cuda-python
```

```null
conda install -c nvidia cuda-python
```

### 自行编译

我没有试过，请参考官方文档：

> [Installation - CUDA Python 12.3.0 documentation](https://nvidia.github.io/cuda-python/install.html "Installation - CUDA Python 12.3.0 documentation")

#### 4、创建环境时预先安装CUDA和cuDNN命令:

也可以在创建环境时，使用命令组合一起预安装：

```null
conda create -n SDW python=3.10.11 cudatoolkit=11.8 cudnn -y
```

"-y"---->过程中默认Yes同意。

这将在创建虚拟环境时，预先在虚拟环境安装好CUDA和cuDNN，换句话说，就是创建一个有CUDA和cuDNN的虚拟环境。

安装较稳定的版本（比如11.8及以下版本）不容易在安装中及后续环境使用和安装包的流程中报错！

#### 5、CUDA和cuDNN升降级:

也同样可以用**Anaconda Navigator**窗口界面进行操作。

##### a）升级

如果没有特殊的要求，也可以用以下命令进行简单的升级：

这将升级环境中的兼容的所有可升级的包。

如果只想升级cuda和cudnn相关的包，则：

举例：假如环境中的cuda是11.7版本，想要或需要升级到11.8或12.1的话，需要cuda和cudnn一起匹配升级：

###### 默认升级

默认升级到最新的与环境匹配兼容的版本：

```null
conda update cudatoolkit cudnn
```

###### 或者指定版本：

```null
conda update cudatoolkit=12.1 cudnn
```

###### 如果升级出错，最好先卸载，再升级：

卸载命令：

######  卸载CUDA Toolkit：

```null
conda uninstall cudatoolkit=11.7
```

###### 卸载cuDNN：

##### b）降级

举例：假如环境中的cuda是12.1版本，想要或需要升级到11.8或11.7的话，需要cuda和cudnn一起匹配降级，最好是先卸载，然后再指定安装成想要或需要的版本：

###### 卸载CUDA Toolkit：

```null
conda uninstall cudatoolkit=12.1
```

###### 卸载cuDNN：

###### 安装指定降级版本的cuda和cudnn：

```null
conda update cudatoolkit=11.8 cudnn
```

```null
conda update cudatoolkit=11.7 cudnn
```

**注意：以上及本文中提到所有操作都必须在自己所要修改的环境中进行，激活进入对应虚拟环境后再进行操作！**

#### 6、如果出现未知错误的解决办法之一

 要清除conda的包缓存以消除未知错误，我们可以使用\`conda clean\`命令。这个命令可以帮助我们清理不再需要的包缓存、索引缓存、tar包等，从而释放磁盘空间并可能解决一些安装或更新包时遇到的问题。以下是一些常用的\`conda clean\`命令选项：

##### a） 清除所有缓存文件和无用的包：

conda clean --all（简单粗暴清理全部缓存和无用的包）

![](https://i-blog.csdnimg.cn/blog_migrate/40e29a8ba0901534c8b11dabd3aa3ed5.png)

  
   这个命令会请求确认，因为它会删除所有缓存的包和索引文件。

##### b）仅清除未使用的包：

conda clean --packages

这个命令会删除那些没有在任何环境中被硬链接的包。

##### c）清除已下载的包文件（tarballs）：

conda clean --tarballs

##### d）清除索引缓存：

conda clean --index-cache

```null
conda clean --index-cache
```

##### e）清除所有可写的包缓存：

conda clean --force-pkgs-dirs

```null
conda clean --force-pkgs-dirs
```

这个命令会删除所有可写的包缓存目录，这可能会影响那些使用软链接到包缓存的环境。

![](https://i-blog.csdnimg.cn/blog_migrate/5315b435171c1a0f6330bc5bceaf476d.png)

在使用这些命令之前，请确保我们了解它们的影响，因为清除缓存可能会导致conda重新下载包，这可能会消耗更多的时间和网络资源。如果我们只是想尝试解决特定的错误，可以先尝试使用\`--all\`选项，因为它是最全面的清理选项。

在执行这些清理操作后，如果遇到问题，可以尝试更新conda到最新版本，或者更换conda的镜像源，以确保能够访问到最新的包索引。如果问题依然存在，可能需要更详细地检查错误信息，或者寻求社区的帮助。

五、验证CUDA、cuDNN和PyTorch安装是否成功
----------------------------

### （一）进入虚拟环境，打开python环境窗口，输入命令进行验证：

```null
Python 3.10.6 | packaged by conda-forge | (main, Oct 24 2022, 16:02:16) [MSC v.1916 64 bit (AMD64)] on win32Type "help", "copyright", "credits" or "license" for more information.>>> print(torch.__version__)
```

如下图所示：

![](https://i-blog.csdnimg.cn/blog_migrate/9dff9acb3ac22aef61a3308257a36dbf.png)

### **（二）完整验证命令如下：** 

在python环境中运行，可以整段复制后直接整段粘贴到python命令行窗口中

包括验证CUDA、cuDNN、PyTorch

```null
device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")print("CUDA 可用：", torch.cuda.is_available())print("cuDNN 已启用：", torch.backends.cudnn.enabled)device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")print("CUDA available:", torch.cuda.is_available())print("cuDNN enabled:", torch.backends.cudnn.enabled)
```

或者使用叠加简化过后的完整验证命令（省去重复导入torch库的步骤）：

```null
device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")  print("CUDA 可用：", torch.cuda.is_available())  print("cuDNN 已启用：", torch.backends.cudnn.enabled)  device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")  print("CUDA available:", torch.cuda.is_available())  print("cuDNN enabled:", torch.backends.cudnn.enabled)  print(torch.version.cuda)  print(torch.backends.cudnn.version())  
```

如果输出验证截图如下，则CUDA、cuDNN、PyTorch安装成功：

![](https://i-blog.csdnimg.cn/blog_migrate/63931cf93f0217bb17d5fee6ec9fb1af.png)

### （三）验证方法可以参考本站以下文章：

> [记录 Windows11安装支持CUDA12.3的Pytorch版本，验证PyTorch是否安装成功\_cuda12.3对应的pytorch版本-CSDN博客](https://blog.csdn.net/u014451778/article/details/134838998?ops_request_misc=&request_id=&biz_id=102&utm_term=CUDA%2012.3&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-134838998.142%5Ev99%5Epc_search_result_base1&spm=1018.2226.3001.4187 "记录 Windows11安装支持CUDA12.3的Pytorch版本，验证PyTorch是否安装成功_cuda12.3对应的pytorch版本-CSDN博客")

### （四）查询conda虚拟环境中的CUDA版本：

在已激活的conda环境中进入Python环境，我们可以使用Python的torch库（如果已经安装）来查询CUDA版本：

import torch  
print(torch.version.cuda)

```null
print(torch.version.cuda)
```

这将返回CUDA的版本号。

![](https://i-blog.csdnimg.cn/blog_migrate/466d5acc3c5481df24d1056a555f9c98.png)

### （五）查询conda虚拟环境中的cuDNN版本：

如果我们正在使用PyTorch，并且已经安装了cuDNN，那我们可以在Python环境中查询cuDNN版本：

import torch  
print(torch.backends.cudnn.version())

```null
print(torch.backends.cudnn.version())
```

这将返回cuDNN的版本号。

![](https://i-blog.csdnimg.cn/blog_migrate/1455056d0acc08039cff16f083ea3abe.png)

请注意，确保在具有CUDA和cuDNN支持的环境中运行这些命令，否则可能会找不到相关的命令或库。

当然，在Windows系统上查询验证CUDA和cuDNN版本还另外几种方法：

\### 查询CUDA版本：

\## 在Windows上##：

1\. 打开命令提示符（CMD）或PowerShell。  
2\. 输入以下命令并按回车键：

 nvcc --version

这将显示CUDA的版本信息。 

`nvlink` 是 NVIDIA 提供的一个链接器工具，它是 CUDA 工具包的一部分，用于将经过 `nvcc` 编译后的 CUDA 模块（`.obj` 或 `.o` 文件）高效地连接起来，形成一个可执行程序或动态链接库。当我们在命令行中执行 `nvlink --version` 时，其主要作用是显示当前安装的 `nvlink` 工具的版本信息，这有助于开发者了解其所使用的 NVIDIA CUDA 编译器工具链的具体版本，进而确保与CUDA库、驱动程序和其他依赖项之间的兼容性。输出信息通常会包括 NVIDIA CUDA Compiler 驱动的版本号以及其他相关信息。

\### 查询cuDNN版本：

\## 在Windows上##：

1\. 找到cuDNN的安装目录，通常位于：

\`C:\\Program Files\\NVIDIA GPU Computing Toolkit\\CUDA\\v<version>\\include\`，

其中\`<version>\`是我们的CUDA版本号。  
2\. 在该目录下，找到并打开\`cudnn\_version.h\`文件。  
3\. 在这个文件中，我们会看到类似于以下的定义：

这里的“CUDNN\_MAJOR”、“CUDNN\_MINOR”和“CUDNN\_PATCHLEVEL”定义了cuDNN的版本号。例如，上述定义表示cuDNN版本为8.2.0。

### （六）如果打印出正在使用的设备是"cpu"

```null
>>> device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")
```

因为我的系统全局中，同时安装了CUDA12.3和对应的cuDNN，还安装有CUDA11.8和对应的cuDNN，11.8版本是后来安装，所以变量自动设置成11.8版本优先。

所以当我在conda环境中安装高于11.8版本的CUDA和cuDNN时，会因为版本冲突无法调用cuda0从而导致打印出“cpu”

![](https://i-blog.csdnimg.cn/blog_migrate/d39fd1ef9dfc5188e3caa9cc1985d013.png)

如果出现这种情况，则要检查系统全局的环境变量，由于系统全局环境变量中的 CUDA 路径优先于 conda 环境中的路径，导致 PyTorch 使用了 11.8 版本的 CUDA，而非我期望的 12.3 版本。

根据我截图中的系统变量设置信息，以下是导致 PyTorch 无法识别 CUDA 设备的原因：

#### **1、如果是系统环境变量优先级冲突:**

由于系统全局环境变量中的 CUDA 路径优先于 conda 环境中的路径，导致 PyTorch 使用了 11.8 版本的 CUDA，而非我们期望的 12.3 版本。

##### **排查和解决方案:**

###### **方法一：修改系统环境变量**

1.  打开 **系统属性** > **高级系统设置** > **环境变量**。
2.  在 **系统变量** 中找到 **CUDA\_PATH** 和 **PATH** 变量。
3.  将 **CUDA\_PATH** 和 **PATH** 变量中的 11.8 版本路径修改为 12.3 版本路径。
4.  **保存** 修改并 **重启** 计算机。

![](https://i-blog.csdnimg.cn/blog_migrate/032359898b4a1cb4cbf53531d8f7274a.png)

###### **方法二：创建新虚拟环境**

1、使用 conda 创建一个新的虚拟环境，并指定 Python 版本和所需的 [CUDA 版本](https://so.csdn.net/so/search?q=CUDA%20%E7%89%88%E6%9C%AC&spm=1001.2101.3001.7020)。例如：

```null
conda create -n new python=3.10.6 cudatoolkit=11.8 cudnn

```

2、激活虚拟环境：

3、在虚拟环境中安装 PyTorch 和其他依赖项。

###### **方法三：使用 pip 安装特定版本的 PyTorch**

1.  卸载现有的 PyTorch 安装。
2.  使用 pip 安装特定版本的 PyTorch，并指定所需的 CUDA 版本。例如：

```null
pip install torch==1.13.1+cu123

```

###### **注意:**

*   修改系统环境变量可能会影响其他应用程序，请谨慎操作。
*   创建虚拟环境是推荐的解决方案，因为它可以隔离不同项目的依赖项和环境配置。
*   使用 pip 安装特定版本的 PyTorch可能需要额外配置环境变量。

#### **2、 其他可能原因:**

*   **CUDA 和 cuDNN 版本不兼容:** 请确保您的 CUDA 和 cuDNN 版本相互兼容。您可以参考 NVIDIA 的 CUDA 兼容性指南: [CUDA Compatibility :: NVIDIA Data Center GPU Driver Documentation](https://docs.nvidia.com/deploy/cuda-compatibility/ "CUDA Compatibility  :: NVIDIA Data Center GPU Driver Documentation")
*   **缺少必要的库:** 请确保您已经安装了所有必要的 CUDA 和 cuDNN 库。

##### **建议:**

*   提供更详细的系统信息和错误信息，以便更好地诊断问题。
*   参考 PyTorch 和 CUDA 官方文档，获取更多安装和配置信息。

##### **以下是一些可能对您有帮助的资源:**

*   PyTorch 官方文档: [Page Redirection](https://pytorch.org/docs/ "Page Redirection")
*   CUDA 官方文档: [CUDA Toolkit Documentation 12.3 Update 2](https://docs.nvidia.com/cuda/ "CUDA Toolkit Documentation 12.3 Update 2")
*   NVIDIA CUDA Compatibility Guide: [CUDA Compatibility :: NVIDIA Data Center GPU Driver Documentation](https://docs.nvidia.com/deploy/cuda-compatibility/ "CUDA Compatibility  :: NVIDIA Data Center GPU Driver Documentation")

希望以上信息能够帮助您解决问题。

六、小结
----

小结一下用conda管理环境和安装CUDA、cuDNN、numpy、PyTorch：

### 1、兼容性较好：

python项目使用conda进行环境管理和包安装还是很有益的，因为conda内置了大量大佬们验证过并上传到渠道中的包，能保证兼容性，不用像其他包管理器一样需要再手动去大量解决依赖冲突问题，速度可能比较慢，但是稳妥；

### 2、灵活性较好：

某些条件下，举个例子：比如项目需要onnxruntime或XFormers库等软件包和依赖，但onnxruntime或XFormers库等不支持CUDA12.3和cuDNN下的torch库的情况下，可以在conda环境中，灵活便捷的切换到CUDA11.8版本和对应的cuDNN版本，具体操作是先卸载conda环境中的CUDA12.3和cuDNN，然后再重新安装CUDA11.8版本和对应的cuDNN版本，整个过程比较丝滑和顺畅，不必再在WIN系统全局中折腾CUDA和cuDNN版本和系统环境变量。这点还是比较方便的。

### 3、其他优点：

当然conda环境还有很多其他便捷的地方，比如升级环境中python版本和软件包版本等等，因篇幅和记述焦点有限，就不在此处一一赘述啦。

**具体使用什么方法管理和安装CUDA和cuDNN还有PyTorch，仁者见仁，智者见智，请根据各人习惯来，仅记录回顾和供参考和学习交流，谢谢！**

### 4、缺点描述：

当然缺点也有很多，比如安装速度较慢，运行性能较慢等等等，因篇幅和记述焦点有限，就不在此处一一赘述啦。

下表比较了 PyPy、Conda 和其他解释器的性能：

| 解释器 | 速度 | 内存使用 | 兼容性 | 优势 | 劣势 |
| --- | --- | --- | --- | --- | --- |
| PyPy | 最快 | 中等 | 兼容 CPython | 高性能 | 可能不完全兼容 CPython，内存使用略高 |
| CPython | 默认 | 最少 | 完全兼容 | 完全兼容 | 速度较慢 |
| Jython | 慢 | 中等 | 兼容 Java | 可移植到 Java 平台 | 速度较慢 |
| IronPython | 慢 | 中等 | 兼容 .NET | 可移植到 .NET 平台 | 速度较慢 |

表格来自Google Gemini，仅供参考。

总之一句话，适合自己的才是最好的，适合项目的也是最好的，兼容性最好的也是最好的。

七、另外的CUDA和cuDNN解决方案
-------------------

另外的CUDA和cuDNN解决方案就是，在系统里安装多个版本的对应CUDA和cuDNN

比如，安装CUDA12.3和cuDNN8.9之后，项目不能正常支行，需要更低的CUDA和cuDNN版本，可以再次在WIN系统全局中安装项目兼容版本的CUDA和cuDNN，并且一定要同样的添加系统环境变量，然后再把所需要的变量往上移，比如移动到CUDA12.3的路径之上，方便直接调用。

举个例子：

在WIN系统全局中分别安装：

CUDA12.3和cuDNN8.9

CUDA12.1和cuDNN8.2

CUDA11.8和cuDNN8.0

CUDA11.7和cuDNN8.0

……

**CUDA和cuDNN的对应关系仅供参考！**

**在这里仅是举例说明**

在Windows系统中安装CUDA和cuDNN时，理论上可以为不同的项目或环境安装不同版本的CUDA和cuDNN组合。然而，通常在同一系统全局环境下同时安装多个CUDA版本会比较复杂，因为CUDA安装程序通常会将binaries添加到系统路径，并且CUDA的安装是全局性的，而不是针对特定项目的局部安装。

尽管如此，我们可以通过以下方式实现不同CUDA与cuDNN版本的共存：

1.  **手动管理路径**：在安装过程中或者安装后通过修改系统环境变量（如PATH），确保每个CUDA版本的bin目录分别对应正确的cuDNN库文件。启动不同项目时，动态切换CUDA的路径指向相应的版本。
    
2.  **使用虚拟环境**：在Python环境中，可以为每个项目创建独立的conda环境或virtualenv，并在这些环境中配置对应的CUDA和cuDNN版本。这样可以在不同环境中隔离不同版本的CUDA/cuDNN。
    

对于上边给出仅供参考的版本组合：

*   | CUDA 版本 | 兼容的 cuDNN 版本 |
    | --- | --- |
    | 12.3 | 8.9, 8.10, 8.11 |
    | 12.2 | 8.2, 8.3, 8.4, 8.5, 8.6, 8.7, 8.8, 8.9, 8.10, 8.11 |
    | 12.1 | 8.2, 8.3, 8.4, 8.5, 8.6, 8.7, 8.8, 8.9, 8.10, 8.11 |
    | 11.8 | 8.0, 8.1, 8.2, 8.3, 8.4, 8.5, 8.6, 8.7, 8.8, 8.9, 8.10, 8.11 |
    | 11.7 | 8.0, 8.1, 8.2, 8.3, 8.4, 8.5, 8.6, 8.7, 8.8, 8.9, 8.10, 8.11 |
    

表格来自Google Gemini，仅供参考。

它们之间的cuDNN版本兼容性**基本上**是对的，因为cuDNN 8.9支持CUDA 11.x系列及以上的版本，同时也支持CUDA 12.x的部分版本。不过，实际操作中需要确认NVIDIA官方文档提供的兼容性矩阵来确保所选CUDA和cuDNN版本确实可以配合使用。

在实践中，为了避免冲突和管理复杂性，建议根据项目需求选择一个稳定的版本组合，并尽可能保持系统的简洁性。如果确实需要在一台机器上安装多种CUDA/cuDNN版本组合，**请查阅最新的NVIDIA官方指南和社区最佳实践来进行操作**。

*   上表仅列出了最新的 CUDA 和 cuDNN 版本。有关较旧版本的兼容性信息，请参阅 NVIDIA 文档。
*   虽然较新的 cuDNN 版本通常可以与较旧的 CUDA 版本一起使用，但建议您使用匹配的 CUDA 和 cuDNN 版本。

**参考资料**

八、conda虚拟环境备份
-------------

对已完善的虚拟环境进行重要修改和尝试修改之前，非常建议我们先进行备份后 再进行操作！

要备份当前的Conda虚拟环境，我们可以使用以下步骤：

1\. 首先，打开终端（在Windows上是Anaconda Prompt）并激活我们想要备份的虚拟环境。使用以下命令：  
 conda activate your\_virtual\_env

```null
conda activate your_virtual_env

```

  其中 “your\_virtual\_env”是我们想要备份的虚拟环境的名称。

2\. 然后，使用 \`conda env export\` 命令将环境的配置信息导出到一个“.YAML”文件中。这个文件将包含所有安装的包及其版本信息。运行以下命令：

conda env export > environment.yml

```null
conda env export > environment.yml

```

   这将在当前目录下创建一个名为 \`environment.yml\` 的文件。

3\. 最后，我们可以将这个 \`environment.yml\` 文件复制到一个安全的位置，或者上传到云存储服务中，以便在需要时可以轻松访问。

这样，我们就成功备份了我们的Conda虚拟环境。当我们需要在另一台计算机上恢复这个环境时，可以在“.YAML”文件所在目录使用以下命令：  
\`\`\`  
conda env create -f environment.yml

```null
conda env create -f environment.yml

```

  这将根据 \`environment.yml\` 文件中的配置信息创建一个新的虚拟环境。

当然，也可以直接用“Anaconda Navigator”图形界面进行：新建、备份或克隆或导入环境的操作。在上边也可以直接备份环境到云端或本地，必要时，从云端或本地恢复（云端需要先登录）。

![](https://i-blog.csdnimg.cn/blog_migrate/8f22e020e2efef991c5635b448b9c6ed.png)

![](https://i-blog.csdnimg.cn/blog_migrate/a2f1aeb8fe74537bce38ca625d2682e5.png)

“Overwrite existing environment”这个选框，是在Import导入“.YAML”文件时才允许点选的，慎选。

九、在下声明
------

**在Windows11系统上具体使用什么方式方法管理和安装CUDA和cuDNN还有PyTorch等，仁者见仁，智者见智，还是要根据各人习惯来和实际情况来，本文仅作记录回顾供参考和学习交流之用，拙见若有唐突、冒昧、冒犯和不足之处，还请见谅，并恭请不吝赐教和斧正，小编将不胜荣幸并感激之至！**

**文章写的不太工整甚至有点乱，主要是因为我想完整或准确地记述安装中遇到的各种问题和解决方案以供回顾，可能显得令人费解，如果有叙述不明之处，欢迎留言或私信讨论，谢谢。** 

**注意：以上及本文中提到所有操作都必须在自己所要修改的环境中进行，重要虚拟环境资源请进行备份！！！激活进入对应虚拟环境后再进行操作！**

**更多细节和未尽之处，欢迎在评论区留言探讨和补充，谢谢！**
  https://blog.csdn.net/u014451778/article/details/136283099