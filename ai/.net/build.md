[Roslyn 使用 Directory.Build.props 文件定义编译](https://cloud.tencent.com/developer/article/1342410)

* ImportDirectoryBuildTargets
* 合并多个文件
```
  <Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />
```
