https://developer.aliyun.com/article/232839

# 修改 ip 
* 查看Mac getmac
```
物理地址            传输名称
=================== ==========================================================
已禁用              已断开连接
16-35-8C-9D-53-2E   \Device\Tcpip_{95D94929-D482-4EF2-860B-25F4229A6BED}
AC-19-8E-BE-9A-19   媒体已断开连接
```

* HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Class\
  查找 95D949

中新建一个字符串值，命名为NetworkAddress
“16358C9D532E”

自定义设置的MAC地址是有格式规定的，十六进制第2位的值需要是2/6/A/E之一，例如e2-11-34-23-11是可用的MAC地址，01-00-3e-4f-52则可能配置不成功，配置不成功时无线网卡还是使用默认的MAC地址”



https://www.bilibili.com/video/BV1fddHYgEeM/
阿里云的只要5.5元，spaceship的要8元多
你可以选阿里云配置cloudflare，这个方案属于操作配置简单化的方式，cloudflare你会用可以更省
回复 @5iter :我看b站有教程，不过我先看的你的，然后就买了