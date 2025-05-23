### 1. 虚拟环境

### 2. 编译

* 编译扩展包
  python setup.py build_ext --inplace
* python setup.py build_ext --inplace --quiet  可以减少信息输出
* 编译并安装包

Hatchling、Setuptools、Flit、PDM
最新的主流是 Hatchling

python setup.py install

### 3. 打包

* [whl egg包区别](../reference/python_whl_egg.md)

### 4. pip

* [pip修改pip cache的位置](https://blog.csdn.net/lynn_flame/article/details/142990080)
  cache dir
* [如何修改pip全局缓存位置和全局安装包存放路径](https://blog.csdn.net/weixin_51455837/article/details/144720197)
* [CUDA和C++混合编译实现Python扩展](https://blog.csdn.net/weixin_42483745/article/details/127221340)
* 安装包

```
# 将本地项目安装为库，其中 -v 表示 verbose，-e 表示可编辑的
pip install -v -e .
```

# 混合编译

* [C++和python的代码如何相互调用](https://www.zhihu.com/question/468279875/answer/2672324747)
  python调用C/C++有不少的方法，如boost.python, swig, ctypes, pybind11等，这些方法有繁有简，而pybind11的优点是对C++ 11支持很好，API比较简单，比较建议使用Pybind11进行处理。

# vscode
## pylint
* VSCode中默认开启的python语法检查工具是pylint，整体非常好用，但是最近在使用requests库时有一些报错提示，比较苦恼，就是在使用到 requests.codes.ok 时，pylint会提示报错:E1101:Instance of 'LookupDict' has no 'ok' member
  pylintArgs 增加  "--generate-members" 


https://marketplace.visualstudio.com/_apis/public/gallery/publishers/ms-python/vsextensions/vscode-pylance/2024.1.100/vspackage
https://marketplace.visualstudio.com/_apis/public/gallery/publishers/ms-python/vsextensions/python/2024.0.4/vspackage
https://marketplace.visualstudio.com/_apis/public/gallery/publishers/VisualStudioExptTeam/vsextensions/IntelliCode/1.3.2/vspackage