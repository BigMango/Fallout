一、[egg](https://so.csdn.net/so/search?q=egg&spm=1001.2101.3001.7020)文件

Egg是Python中一种旧的包格式，它是通过setuptools工具来创建的。Egg包的文件扩展名为.egg。Egg包包含了[Python模块](https://so.csdn.net/so/search?q=Python%E6%A8%A1%E5%9D%97&spm=1001.2101.3001.7020)、资源文件、依赖关系等。Egg包具有以下特点：

* Egg包可以被easy\_install工具安装和管理。
* Egg包可以包含C扩展模块。
* Egg包可以自动解析依赖关系。

对应的安装方式是：

```
ez_install install _______.egg
或者
# 使用easy_install安装Egg包
easy_install package.egg
```

二、whl文件
-----------

Wheel是Python中一种新的包格式，它是通过wheel工具来创建的。Wheel包的文件扩展名为.whl。相比于Egg包，Wheel包具有以下优点：

* Wheel包更简单、更快速，因为它是一个预编译的二进制包。
* Wheel包可以包含纯Python代码，也可以包含C扩展模块。
* Wheel包支持Python 2和Python 3。

```
# 使用pip安装Wheel包
pip install  _______.whl

示例：pip install package.whl
```

三、扩展
--------

```
python -m pip install --upgrade pip   #pip的更新

pip install 安装包名                  #下载指定的python包

pip install 包名==版本号              #下载指定版本的python包

pip list                           #列出所有已安装的Python包

pip show 安装包名                  # 查看包的信息，包括它的安装位置。

pip list --outdated                  #查询是否有可以更新的包

pip install --upgrade 要更新的包名    #更新指定包

pip uninstall 要卸载的包名            #卸载的python包

pip search 包名               #搜索包，如pip  search matplotlib
```

四、包格式比较
--------------

下表总结了Egg包和Wheel包的比较：

| 特点           | Egg包                          | Wheel包                        |
| -------------- | ------------------------------ | ------------------------------ |
| 打包工具       | setuptools                     | wheel                          |
| 文件扩展名     | .egg                           | .whl                           |
| 安装工具       | easy\_install                  | pip                            |
| 包含内容       | Python模块、资源文件、依赖关系 | Python模块、资源文件、依赖关系 |
| 是否预编译     | 否                             | 是                             |
| 支持Python版本 | Python 2和Python 3             | Python 2和Python 3             |

五、结论
--------

在Python包管理中，Wheel包是更推荐的包格式。它简单、高效，并且支持Python 2和Python 3。如果你要开发Python包并进行分发，建议使用Wheel包进行打包。希望本文对你理解Python包管理有所帮助。

通过本文的介绍，你应该对Python中的包管理有了一定的了解。无论是Egg包还是Wheel包，都是Python包管理的一部分，选择合适的包格式取决于你的需求。希望本文能够帮助你更好地理解Python包管理的重要性。
https://blog.csdn.net/weixin_49114503/article/details/139270516
