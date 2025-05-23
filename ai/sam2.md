
“corecrt.h”: No such file or directory

安装 VS 安装 UniversalCRT搜索crt 即可

'cl.exe' 不是内部或外部命令，也不是可运行的程序
这个问题比较复杂
python setup.py build_ext --inplace
1.在conda命令行测试,不用在vs的终端里面
2.实在不行就看看

D:\ProgramData\miniconda3\envs\sam2\Lib\site-packages\torch\utils\cpp_extension.py 这个目录的文件
``` 
    地方1        
    compile_rule.append(
            '  command = cl /showIncludes $cflags -c $in /Fo$out $post_cflags')

地方2
def get_cxx_compiler():
    if IS_WINDOWS:
        compiler = os.environ.get('CXX', 'cl')
    else:
        compiler = os.environ.get('CXX', 'c++')
    return 'D:/Program Files/Microsoft Visual Studio/2022/Enterprise/VC/Tools/MSVC/14.43.34808/bin/Hostx64/x64/cl'
    # return compiler
```            

还有这个地方
build\temp.win-amd64-cpython-311\Release\build.ninja