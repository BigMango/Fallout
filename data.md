数据关联

一些东西是必定出现的还是随机的,还是几个随机的,是否需要带任务才会出现

物品属于哪个面板

有写地方有多个东西,可以加个count和分类
一些特殊的箱子需要钥匙

### 1. B 社数据结构

https://modding.wiki/en/skyrim/users/bethesda-archives

| Game                   | BSA v100     | BSA v103        | BSA v104     | BSA v105     | BA2 v1     |
| ---------------------- | ------------ | --------------- | ------------ | ------------ | ---------- |
| Morrowind              | Compatible   | Incompatible    | Incompatible | Incompatible | Ignored    |
| Oblivion               | Incompatible | Compatible      | Ignored      | Ignored      | Ignored    |
| Fallout 3              | Incompatible | _Untested_    | Compatible   | _Untested_ | Ignored    |
| Fallout New Vegas      | Incompatible | _Untested_    | Compatible   | _Untested_ | Ignored    |
| Skyrim (2011)          | Incompatible | Limited Support | Compatible   | Incompatible | Ignored    |
| Skyrim Special Edition | Incompatible | Incompatible    | Incompatible | Compatible   | Ignored    |
| Fallout 4              | Ignored      | Ignored         | Ignored      | Ignored      | Compatible |
| Skyrim VR              | Incompatible | _Untested_    | Incompatible | Compatible   | Ignored    |
| Fallout 4 VR           | Ignored      | Ignored         | Ignored      | Ignored      | Compatible |
| Fallout 76             | Ignored      | Ignored         | Ignored      | Ignored      | Compatible |

#### 1.1. B社游戏文件

https://fallout.fandom.com/wiki/Record_file

#### 1.2. ESM

https://www.creationkit.com/fallout4/index.php?title=Data_File

https://modding.wiki/en/skyrim/users/plugin-load-order
https://www.afkmods.com/index.php?/topic/5079-plugin-files-and-you-esmeslesp/
https://github.com/wrye-bash/wrye-bash/issues/426#issuecomment-448718981
https://www.afkmods.com/index.php?/topic/5079-plugin-files-and-you-esmeslesp/page/5/#comment-174631

#### 1.3. 上古卷轴

https://en.uesp.net/wiki/Skyrim_Mod:Archive_File_Format#Header
https://en.uesp.net/wiki/Skyrim_Mod:Mod_File_Format
https://en.uesp.net/wiki/Oblivion_Mod:Mod_File_Format

### 2. 数据导出

#### 2.1. fo76-dumps

+ Python 环境

pip config --global set global.index-url https://mirrors.aliyun.com/pypi/simple/
pip config --global set install.trusted-host mirrors.aliyun.com

https://pypi.org/project/pandas/1.2.4/#files

swf 调试
https://www.nexusmods.com/fallout4/articles/1728

https://www.youtube.com/watch?v=FCtGk4HpVwY&ab_channel=SkyrimScripting

##### PAS脚本导出

| 数据集合 | 数据量  | 导出时长 |
| -------- | ------- | -------- |
| ids      | 5337803 | 1:41:55  |
|          |         |          |

### 3. 数据解析

#### 3.1. 参考

##### 可能路径

Github的作者[matortheeternal](https://github.com/matortheeternal/)对B社的项目做了很多分析工作。可惜的是还没有到Fallout76就停止的研究。

* [xedit-lib](https://github.com/matortheeternal/xedit-lib) 将xEdit的数据解析部分封装为库。
* [esp.json](https://github.com/matortheeternal/esp.json) 将xEdit的定义生成为Json，不过Generator目录下各个游戏的数据(js文件)不知道是怎么来的。
  [引用1](https://www.reddit.com/r/skyrimmods/comments/sf9oos/espjson_json_record_definitions_for_tes5_sse_tes4/)
* [esper](https://github.com/matortheeternal/esper) 作者停止Delphi的dll后转到了C#独立封装。使用esp.json生成的定义。
* [zedit](https://github.com/z-edit/zedit)调用xedit-lib用Angular 1.8.5 做的Election工具。
* [XeLibSharp](https://github.com/aers/XeLibSharp.git) xedit-lib的C#封装。

##### 第三方库

* [Mutagen](https://github.com/Mutagen-Modding/Mutagen) 一个C#的B社库，没有辐射76应该永远不会有。代码风格很不喜欢，不过提供了大量的可能的参考，目前还经常更新。
