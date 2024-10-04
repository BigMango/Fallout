### 1. 说明

&emsp;&emsp;xEdit用于管理B社的游戏，主要是辐射系列。

    这个是最基础的工具，大量的第三方工具依赖这个工具。基于Delphi 11开发。[源码](https://github.com/TES5Edit/TES5Edit)
    还有一个东西[zedit](https://github.com/z-edit/zedit)
    [Zeditor](https://github.com/AinTunez/Zeditor.git)

### 2. 使用

#### 2.1. 首次运行

[初次运行没有ini的问题](https://github.com/TES5Edit/TES5Edit/issues/812)

    注册表文件:

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Fallout 76]
"Path"="D:\\Program Files (x86)\\Steam\\steamapps\\common\\Fallout76\\"
"UninstallString"="\"C:\\Program Files (x86)\\Steam\\steam.exe\" steam://uninstall/1151340"
```

* [官方说明](https://stepmodifications.org/wiki/Guide:XEdit)
* [日文说明](https://thinkingskeever.hatenablog.com/entry/2018/01/12/160206)

### 3. 脚本

&emsp;&emsp;大量的第三方工具都是基于这个设计器，数据的导出使用pascal动态的脚本来实现。
这里有个问题就是怎么调试动态脚本。

### 4. Delphi

    默认是用RAD 11开发的，对应的包是28。RAD 12有的库可能不支持，默认的包是29。
    Delphi有时候会莫名其妙的出现Socket Error错误。

    [详情](https://en.delphipraxis.net/topic/4535-delphi-1041-socket-error-on-ide-start/)

```
    HKEY_CURRENT_USER\SOFTWARE\Embarcadero\BDS\22.0\Known IDE Packages
    备注前面加两个下划线即可--> "__Embarcadero FireUI Live Preview Package"
```

  BPL 无法安装，Delphi 11 有时候会可以编译但是不能安装BPL，不知道为什么，但是安装了DevExpress以后就可以了。

### 5. 调试	

    为了启动的时候就可以是辐射76，在Option的Debugger的Param下设置

```
-FO76 -D:"D:\Program Files (x86)\Steam\steamapps\common\Fallout76\Data\"
-FO76 -D:"E:\SteamGames\steamapps\common\Fallout76\Data\"
```
