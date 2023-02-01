# Nriver的scoop bucket 仓库

Scoop是Windows下的包管理器，使用scoop可以很方便的安装和更新软件。如果没有安装scoop，可以参考下面的 [安装scoop](#安装scoop)
章节

添加源

```
scoop bucket add Scoop-Nriver https://github.com/nriver/Scoop-Nriver
```

安装软件, 比如安装 Trilium Notes 中文版

```
scoop install trilium-cn
```

# 安装scoop

在powershell里运行以下命令

```
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
iwr -useb get.scoop.sh | iex
```

如果不想安装在c盘，可以用以下命令安装scoop

```
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
$env:SCOOP='E:\soft\scoop'
[environment]::setEnvironmentVariable('SCOOP',$env:SCOOP,'User')
iwr -useb get.scoop.sh | iex
```

(如果网络有问题，可以手动将 get.scoop.sh 的文件下载保存为install.ps1，然后把`iwr -useb get.scoop.sh | iex`
改成 `.\install.ps1` 再安装)

## scoop使用代理安装和更新软件

网络环境不好可以尝试使用`proxychains`来让命令行程序通过代理联网

安装`proxychains`

```
scoop install proxychains
```

找到配置文件`proxychains.conf`，比如`E:\soft\scoop\persist\proxychains\proxychains.conf`

开启代理

```
proxychains -q powershell
```

之后所有的命令的网络请求都会通过代理发送, 比如更新所有程序

```
scoop update *
```
