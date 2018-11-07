# 安装IPFS
有多种方法可以在系统上安装IPFS副本。我们通常建议安装预先构建的软件包，但以下是一些其他支持的选项：

* 从预构建包安装（推荐）
* 使用ipfs-update进行安装
* 从源头构建
* 升级IPFS
* 故障排除

`请注意，这些说明都使用命令行。我们$用来指示命令提示符 - 要键入的命令位于带有前缀的行上，而输出行没有前缀。`

## 从预构建包安装
首先，为您的平台下载正确版本的IPFS：

[下载适用于您的平台的IPFS](https://dist.ipfs.io/#go-ipfs) 

### MacOS和Linux

下载后，解压缩归档文件，然后使用脚本将ipfs二进制文件移动到可执行文件$PATH中的某个位置install.sh：
```sh
$ tar xvfz go-ipfs.tar.gz
$ cd go-ipfs
$ ./install.sh
```

测试出来：

```sh
$ ipfs help
USAGE:

    ipfs - Global p2p merkle-dag filesystem.
...
```

恭喜！您现在在计算机上安装了有效的IPFS。

[一般用法](./usage.md)   

### windows
下载后，解压缩存档，然后移动ipfs.exe 到您的存档中%PATH%。

测试出来：
```sh
$ ipfs help
USAGE:

    ipfs - Global p2p merkle-dag filesystem.
...
```
恭喜！您现在在计算机上安装了有效的IPFS。

一般用法   

## 使用ipfs-update进行安装

ipfs-update是一个用于安装和升级ipfs二进制文件的命令行工具。

### 获取ipfs-update

ipfs-update可以在以下网址下载适用于您的平台：https：//dist.ipfs.io/#ipfs-update


如果您有一个正常工作的Go环境（> = 1.8），您也可以使用以下命令安装它：

```sh
$ go get -u github.com/ipfs/ipfs-update
```
安装新版本ipfs或升级时，请确保使用的是最新版本ipfs-update。

### 使用ipfs-update安装ipfs
ipfs-update versions列出ipfs可供下载的所有可用版本：
```sh
$ ipfs-update versions
v0.3.2
v0.3.4
v0.3.5
v0.3.6
v0.3.7
v0.3.8
v0.3.9
v0.3.10
v0.3.11
v0.4.0
v0.4.1
v0.4.2
v0.4.3
v0.4.4
v0.4.5
v0.4.6
v0.4.7-rc1
```

ipfs-update install latest 将安装最新的可用版本：

```sh
$ ipfs-update install latest
fetching go-ipfs version v0.4.7-rc1
binary downloaded, verifying...
success!
stashing old binary
installing new binary to /home/hector/go/bin/ipfs
checking if repo migration is needed...
Installation complete!
```

`请注意，最新的可用版本可能不稳定（即表单中的候选版本vX.X.X-rcX）。因此，建议指定要安装的版本，例如：ipfs-update install v0.4.6。`

## 使用源码构建
`警告：过去您可以使用安装IPFS go get。这不再起作用了！`
如果需要，还可以从源代码构建IPFS。如果您使用的是Mac OS X或Linux，请查看[自述文件](https://github.com/ipfs/go-ipfs#build-from-source)以获取安装说明。如果您在Windows上，请查看[此文档](https://github.com/ipfs/go-ipfs/blob/master/docs/windows.md)以获取说明。

### 使用ipfs-update升降级
ipfs升级（和降级）可能涉及[fs-repo-migrations](https://dist.ipfs.io/#fs-repo-migrations)工具执行的存储库升级过程 。

#### 使用ipfs-update升级
ipfs-update install将fs-repo-migrations在安装新版本或旧ipfs版本时（如上所述）在需要时下载并运行。这是最简单的升级方式。

`警告：确保在升级期间未运行ipfs守护程序`
#### 手动升级
要执行手动升级ipfs，您需要手动运行任何存储库迁移。程序如下：
* ipfs如果守护程序正在运行，请将其停止
* （可选）备份ipfs数据文件夹（即cp -aL ~/.ipfs ~/.ipfs.bk）
* ipfs从https://dist.ipfs.io/#go-ipfs下载并安装最新版本
* 运行ipfs daemon。
当需要存储库迁移时，ipfs将通知用户，下载并安装fs-repo-migrations 并执行升级。如果希望过程无人值守，请使用--migrate 标志启动守护程序。

也可以通过fs-repo-migrations 从https://dist.ipfs.io/#fs-repo-migrations下载最新版本并 按照[这些说明](https://github.com/ipfs/fs-repo-migrations/blob/master/run.md)手动运行迁移。

## 故障排除
### 帮助
如果您有任何问题，请在[#ipfs](https://docs.ipfs.io/introduction/#community)或通过[邮件列表](https://docs.ipfs.io/introduction/#community)获取实时帮助 。

### 检查Go版本
IPFS适用于Go 1.7.0或更高版本。要检查已安装的版本，请键入go version。这是我得到的：
```sh
$ go version
go version go1.7 linux/amd64
```
如果需要更新，建议从规范的Go包安装 。包管理器通常包含过时的Go包。

### 安装FUSE
有关设置FUSE的更多详细信息（以便可以挂载文件系统），请参阅 github.com/ipfs/go-ipfs/blob/master/docs/fuse.md

