### 1. 说明

    本文说明辐射游戏(Fallout 76)数据处理的一些情况。

### 2. 开发

#### 2.1. 地图

    目前大量的地图都是基于[Leaflet](https://github.com/Leaflet)，这个js的，当然也有ts的封装，目前在vue、react、angular、blazor上都有封装。

#### 2.2. 地图切片

    为了减小网络开销，地图提供多个分辨率的切片图，一般提供5-7级的缩放大小。

+ [MapTileCutter](https://github.com/jeanropke/MapTileCutter)
  ![图片](https://raw.githubusercontent.com/jeanropke/MapTileCutter/main/Images/Screenshot.png)
+ [BaiduMapTileCutter](https://github.com/jiazheng/BaiduMapTileCutter) 百度地图切图工具

#### 2.3. Leaflet

+ [React](https://github.com/PaulLeCam/react-leaflet)
+ [Leaflet Map for Blazor](https://github.com/ichim/LeafletForBlazor-NuGet) 有一些基础工具

#### 2.4. Mapsui

  https://software-notion.de/apps/breath-companion

#### 2.5. 地图参考

+ [原神源码](https://github.com/kongying-tavern/yuan-shen-map) [在线](https://v3.yuanshen.site/) [更新引擎](https://github.com/kongying-tavern/yuanshendt-updater) [自研地图引擎](https://github.com/kongying-tavern/lightweight-genshin-maps)

### 3. 相关工具

#### 3.1. xEdit

    这个是最基础的工具，大量的第三方工具依赖这个工具。基于Delphi 11开发。[源码](https://github.com/TES5Edit/TES5Edit)

    [初次运行没有ini的问题](https://github.com/TES5Edit/TES5Edit/issues/812)
    注册表文件:

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Fallout 76]
"Path"="D:\\Program Files (x86)\\Steam\\steamapps\\common\\Fallout76\\"
"UninstallString"="\"C:\\Program Files (x86)\\Steam\\steam.exe\" steam://uninstall/1151340"
```

    [日文说明](https://thinkingskeever.hatenablog.com/entry/2018/01/12/160206)

#### 3.2. .net 工具
+ 最新工具 [源码](https://github.com/AlexxEG/BSA_Browser) 还比较原始。

+ 的过时工具

    https://github.com/demonixis/ESMSharp

    https://github.com/CaptainSaveACode/Fallout.NET

#### 3.4. Mappalachia 地图管理工具

    [源代码](https://github.com/AHeroicLlama/Mappalachia)

+ 主地图:提供一个完整的主地图，版本未知。
+ 小地图里面有主地图和大量的小地图，不过辐射76在小地图里面是不支持地图导航的，这样小地图只是看看而已

#### 3.5. Fallout 76 dumps

    数据导出的工具，基于Python和Pascal实现。[源码](https://github.com/FWDekker/fo76-dumps)

#### 3.6. fo76utils

    基于C++的数据导出工具。

### 4. 数据说明

### 5. 参考资源

辐射76 QQ 机器人 https://github.com/wssy001/fallout76-public

资源翻译 https://translate.rdo.gg/

古老的一套代码 https://github.com/matortheeternal/smash

#### 5.1. 百科

+ [reddit](https://www.reddit.com/r/fo76/wiki/resources/)
+ [biligame](https://wiki.biligame.com/)

#### 5.2. 地图

+ [RDR2CollectorsMap](https://github.com/jeanropke/RDR2CollectorsMap)  实现了一个完美的有戏地图
+ [写了个老头环互动地图的网站](http://bbs.nga.cn/read.php?tid=30914203) [源代码](https://github.com/elpwc/EldenRingOnlineMap) 有多端的列子
+ [原神辅助怪物采集物雷](https://github.com/red-gezi/GenshinImpact_MonsterMap)
+ [原神地图](https://wiki.biligame.com/ys/%E5%8E%9F%E7%A5%9E%E5%9C%B0%E5%9B%BE%E5%B7%A5%E5%85%B7_%E5%85%A8%E5%9C%B0%E6%A0%87%E4%BD%8D%E7%BD%AE%E7%82%B9) 提供一个游戏地图和客户端比对的一个方法

### 6. 第三方组织

+ https://github.com/orgs/kongying-tavern 国人组织，有大量地图相关的开发人员的相关作品
