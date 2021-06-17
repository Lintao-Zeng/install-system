# install-system

不使用U盘安装Linux系统，首先安装https://github.com/noryb009/lick
这样就可以使用grub启动器来引导系统
将下载好的iso镜像文件随便放入一个磁盘分区
然后再新建一个分区并格式化为FAT32格式，用软碟通将iso镜像中的所有文件提取到此分区（这一步是因为某些Linux在安装时还需要安装介质，否则不允许安装）

做完之后重启进入grub启动器，按c进入命令行，输入ls查看所有磁盘分区，ls (hdx,y)/命令可以查看分区详情
接着使用grub的回放技术将iso镜像文件挂在到loop，参考：https://blog.csdn.net/qq_42748849/article/details/81273703
接下来会进入Linux的安装引导界面，某些Linux安装程序会提示找不到安装介质，不用慌，我们进入shell命令行
将刚才设置的FAT32分区挂在到/cdrom目录就可以继续安装了

参考命令：

安装介质都是使用FAT32格式

mount /dev/sdb3 /cdrom

mount -t vfat /dev/sdb3 /cdrom

mount -t ntfs /dev/sdb3 /cdrom

mount -t ext4 /dev/sdb3 /cdrom

umount /cdrom
