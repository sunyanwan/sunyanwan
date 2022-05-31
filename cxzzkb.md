常 http://web.tecxz.com:9080/student/mkdocs/linuxbook/index.html

贴图：

1.将左侧库中虚拟机名改为自己的学号(21092330123)，指定磁盘容量（5分）（并贴图） 40 单个 （安装好，打开编辑截图，并贴图）（5分）

贴图：

2.到虚拟机设置选项高级中选择UEFI固件类型（3分）（并贴图）

选项 高级 UEFI 确定

2.贴图：

到设置你的姓名your name完（your name：ubuntu

Your computer’s name:学号

password：123456）（并贴图）

贴图：

安装好虚拟机，打开终端（贴图）（5分）

3.截图：

到换完源完（用focal的源）并更新（5分）（并贴图）

浏览器 阿里云的源 山上小和尚


deb http://mirrors.aliyun.com/ubuntu/ focal main 

deb http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted

deb http://mirrors.aliyun.com/ubuntu/ focal universe

deb http://mirrors.aliyun.com/ubuntu/ focal-updates universe

deb http://mirrors.aliyun.com/ubuntu/ focal multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-updates multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-security main restricted

deb http://mirrors.aliyun.com/ubuntu/ focal-security universe

deb http://mirrors.aliyun.com/ubuntu/ focal-security multiverse




sudo gedit /etc/apt/sources.list （粘贴进去截图）

sudo apt update

4.安装ssh（3分）（并贴图）

ssh

sudo apt install openssh-server

sudo systemctl restart sshd

sudo systemctl status sshd

sudo systemctl enable sshd

截图：

ssh ubuntu@localhost yes （截图）

exit加回车退回正确系统

ssh ubuntu@localhost

ctrl加D退回之前系统

7.贴图：

5.添加一块新的虚拟盘（3分）（并贴图）

设置 添加 硬盘（第一个） scsl 存储save 确定 sudo reboot

贴图：

lsblk 

贴图：

6.添加两个新的分区（5分）（并贴图）

sudo apt install gdisk

sudo gdisk /dev/sdb o y p s n 回车 回车 （last sector）+512M

(Hex 8300) ef00 n 回车回车回车 p s w y

sudo gdisk /dev/sdb p s c 1 syzesp c 2 syroot w y

贴图：

sudo gdisk /dev/sdb p （贴图） q(退出）


7.挂载sdb1,sdb2（4分）（并贴图）

sudo mkfs.vfat -F32 /dev/sdb1

sudo mkfs.ext4 /dev/sdb2 y

sudo mkdir /mnt/usb

sudo mount /dev/sdb2 /mnt/usb

sudo mkdir /mnt/usb/boot/efi -p

sudo mount /dev/sdb1 /mnt/usb/boot/efi/

贴图：

lsblk 

8.下载Linux镜像文件（5分）（并贴结果图）

sudo apt install debootstrap

sudo debootstrap --arch=amd64 focal /mnt/usb/ https://mirrors.aliyun.edu.cn/ubuntu/

sudo apt install arch-install-scripts

sudo genfstab -U /mnt/usb/ > /mnt/usb/tmp/fstab

sudo cp /etc/apt/sources.list /mnt/usb/etc/apt/

贴图：

ls /mnt/usb/

9.三个挂载（3分）（并贴图）

sudo mount -o bind /dev/ /mnt/usb/dev/

sudo mount -o bind /proc/ /mnt/usb/proc/

sudo mount -o bind /sys/ /mnt/usb/sys/

贴图：

sudo chroot /mnt/usb/


10.到安装完内核（3分）（并贴结果图）

sudo chroot /mnt/usb/ /bin/bash

mv /tmp/fstab /etc/fstab

apt update

apt install linux-image-generic 第二项 

贴图：

sudo chroot /mnt/usb/  (贴图，显示，liux)

useradd ubuntu -m

ls /home/

passwd root （passwd）

passwd ubuntu

apt install vim

visudo

Men admin改成ubuntu ALL %不变 （大写）

将%admin ALL=(ALL:ALL) ALL 改成 %ubuntu ALL=(ALL:ALL) ALL

apt install efibootmgr

apt install grub-efi-amd64

mount -t efivarfs efivarfs /sys/firmware/efi/efivars/

grub-install -v --target=x86_64-efi --recheck /dev/sdb

sudo apt vim

vim /etc/default/grub

白色倒二加个#

在GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"前面加上'#'号

update-grub

12.安装net-tools（3分）

贴图：

apt install net-tools network-manager openssh-server

apt install net-tools (贴图）

退出系统

13.安装ssh（3分）

4.安装ssh（3分）（并贴图）

ssh

sudo apt install openssh-server

sudo systemctl restart sshd

sudo systemctl status sshd

sudo systemctl enable sshd

截图：

ssh ubuntu@localhost yes （截图）

exit加回车退回正确系统

ssh ubuntu@localhost

ctrl加D退回之前系统


贴图：

14.更新引导，进入b系统（7分）（并贴图）

sudo reboot

ubuntu 123456 （截图）


15.更改为bash（3分）（并贴图）

贴图：

chsh -s /bin/bash

16.实现自动分配ip（4分）（并贴图）

bash

sudo vim /usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf

sudo systemctl restart NetworkManager

贴图：

ip a （截图）

sudo apt update

11.安装图形化界面后安装salt-minion完（10分）（并贴图）

sudo apt install tasksel

sudo tasksel

空格选中 tab ok

贴图：

ubuntu desktop (截图）

sudo apt install open-vm-tools (充满)

18.在终端使用搜狗输入法并输入自己的名字（3分）（并贴图）

搜狗输入法 bing.com sougou for liux x86 amd

sudo apt update

sudo dpkg -i sogoup（补全）

sudo apt install -f -y

sudo dpkg -i sogoup（补全）

sudo apt remove --purge ibus* -y

sudo apt install libqt5qml5 libqt5quick5 libqt5quickwidgets5 qml-module-qtquick2

sudo apt install libgsettings-qt1

编辑文件：

vim ~/.xprofile

将下面代码复制进去： 

export XMODIFIERS="@im=fcitx" 

export XIM="fcitx" 

export XIM_PROGRAM="fcitx"

export GTK_IM_MODULE="fcitx"

export QT_IM_MODULE="fcitx"


fcitx &

sudo reboot

方块 co 去掉加号 最低上 sogou

ctrl 加 空格 显示搜狗的时候（截图）

贴图：

打开终端，输入自己的名字

19.在火狐中输入文字（3分）

贴图：

打开火狐，输入文字，截图

20.生成字符集（5分）（并贴图）

配置字符集

1.ubuntu特有的一种方式

sudo dpkg-reconfigure locales

en_us.iso-8859-1

en_us.iso-8859-15 iso-8859-15

zh_CN GB2312

zh_CN.GB18030 GB18030

zh_CN.GBK GBK

zh_CN.UTF-8 UTF-8

tab后回车

en_us

sudo locale-gen

local

vim /etc/enviroment

空一格 加上

LANG=CN

LANGUAGE=zh_cn

LC_CTYPE=“zh_cn.UTF-8"

贴图：

ls

21.安装WPS(4分)（并贴图）

浏览器输入 bing WPS wps Office -Free Office Downloads for pc 进去

右上角Downloads deb

将位置改为桌面

cd Downloads

sudp dpkg -i wps（补全）

点击Activities

搜索wps（一行代表成功）

进入WPS会要求同意一个协议

进去贴图：

22.将文件移到wps-fonts，更新字体（6分）（并贴图）

web.tecxz.com:9080

file

weixin

wps

unzip wps-fonts.zip

ls /usr/share/fonts

sudo mv wps-fonts-master/wps/ /usr/share/fonts/wps-fonts

贴图：

fc-cache -fv （截图）

23.安装微信完（3分）（并贴图）

cd Downloads

贴图：

sudp dpkg -i wei（补全）（截图）

24.安装远程桌面完并能用Windows的远程桌面连接（5分）（并贴图）

sudo apt install xrdp

sudo systemctl restart xrdp

sudo systemctl status xrdp

sudo systemctl enable xrdp

sudo usermod -aG ssl-cert xrdp

sudo vim /ect/xrdp/startwm.sh

蓝色下面 在if test -r 上面添加

Unset DBUS_SESSION_ADDRESS Unset XDG_RUNTINE_DIR

:wq

重启

完成后用windows的远程桌面去连接

ubuntu 123456 

贴图：

桌面里面，跟外面一起，外面打开终端

附加题：1.安装zsh并有自动补全功能（5分）（并贴图）

1.下载zsh：

sudo apt install zsh

2.查看当前系统中可食用的shell：

cat /etc/shells

3.如果没有vim先安装vim：

sudo apt install vim

4.进入passwd以后按a进行编辑将默认的bash换成zsh，然后按ESC，退出编辑模式输入：wq保存：

sudo vim /etc/passwd

5.安装oh-my-zsh用于快速配置zsh，先下载curl：

sudo apt install curl

6.然后安装git：

sudo apt install git

7.从gitee上进入zsh：

sh -c "$(curl -fsSL https://gitee.com/Devkings/oh_my_zsh_install/raw/master/install.sh)"

8.下载自动补全插件：

wget -P ~/.oh-my-zsh/plugins/incr http://mimosa-pudica.net/src/incr-0.2.zsh

9.编辑zshrc:sudo vim ~/.zshrc 把plugins=(git)改成plugins(git zsh-autosuggestions)

10.重启以后并打开终端：zsh

贴图:

输入一个，显示补全（贴图）

2.安装Samba并将搜狗移到windows的文件夹（5分）（并贴图）

安装和配置samba

1.安装samba：sudo apt install samba

2.创建用户:sudo useradd share

3.设置samba口令:sudo smbpasswd -a share

4.建立目录用来存放文件:sudo mkdir /data

5.用用户名目标文件:sudo chown share.share /data

6.删除一个文件:sudo rm /etc/samba/smb.conf

7.打开浏览器搜索web.tecxz.com:9080

file

smb.conf save link as

8.用vim打开文件:vim smb.conf 粘贴

9.将文件移动到samba目录下:sudo mv smb.conf /etc/samba

10.重启服务:sudo systemctl restart smbd.service

11.查看服务状态:sudo systemctl status smbd.service

12.查看当前IP:ip a

13.使smb开机自启:sudo systemctl enable smbd.service

14.在windows中在此电脑中访问ip a //

share 123456

16.将ubuntu中的文件复制到次文件夹中:

sudo cp ../Downloads/sogou /data

17.然后去windows上的文件夹中查看（截图）
