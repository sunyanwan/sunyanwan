常 http://web.tecxz.com:9080/student/mkdocs/linuxbook/index.html

1.到指定磁盘容量完（5分） 40 单个 （并贴图）

2.到虚拟机设置选项高级中选择UEFI固件类型（10分）（并贴图）

选项 高级 UEFI 确定

3.到设置你的姓名your name完（your name：ubuntu

Your computer’s name:学号

password：123456）（5分）（并贴图）

4.到安装完a系统完（10分）（并贴图）

5.到换完源完（用focal的源）并更新（2分）（并贴图）

浏览器 bing.com ubuntu sources.list ustc （8行）

sudo gedit /etc/apt/sources.list （粘贴进去截图）

sudo apt update

6.安装ssh和salt-minion完（3分）（并贴图）

ssh

sudo apt install openssh-server

sudo systemctl restart sshd

sudo systemctl status sshd

sudo systemctl enable sshd

ssh ubuntu@localhost yes （截图）

exit加回车退回正确系统

ssh ubuntu@localhost

ctrl加D退回之前系统

salt-minion

sudo apt update

sudo apt upgrade

sudo apt install salt-minion

sudo vim /etc/salt/minion

master: tecxz.com

使用文本编辑器按a改#master：salt，

将#删除由蓝色变成白色后将salt改为master：tecxz.com,

之后按esc退出编辑模式按：wq

sudo vim /etc/salt/minion_id

sudo systemctl restart salt-minion

sudo systemctl status salt-minion

sudo systemctl enable salt-minion

（自己学号，截图）

7.到挂载完sdb1和sdb2完（10分）（并贴图）

设置 添加 硬盘（第一个） scsl 存储save 确定 sudo reboot

sudo apt install gdisk

sudo gdisk /dev/sdb o y p s n 回车 回车 （last sector）+512M

(Hex 8300) ef00 n 回车回车回车 p s w y

sudo gdisk /dev/sdb p s c 1 syzesp c 2 syroot w y

sudo gdisk /dev/sdb p w y

（查看是否改好）

sudo mkfs.vfat -F32 /dev/sdb1

sudo mkfs.ext4 /dev/sdb2 y

sudo mkdir /mnt/usb

sudo mount /dev/sdb2 /mnt/usb

sudo mkdir /mnt/usb/boot/efi -p

sudo mount /dev/sdb1 /mnt/usb/boot/efi/

lsblk (截图）

8.到安装内核（5分）（并贴图）

sudo apt install debootstrap

sudo debootstrap --arch=amd64 focal /mnt/usb/ https://mirrors.ustc.edu.cn/ubuntu/

sudo apt install arch-install-scripts

sudo mount -o bind /dev/ /mnt/usb/dev/

sudo mount -o bind /proc/ /mnt/usb/proc/

sudo mount -o bind /sys/ /mnt/usb/sys/

sudo apt update

sudo cp /etc/apt/sources.list /mnt/usb/etc/apt/

sudo genfstab -U /mnt/usb/ > /mnt/usb/tmp/fstab

sudo chroot /mnt/usb/ /bin/bash

mv /tmp/fstab /etc/fstab

apt update

apt install linux-image-generic 第二项 （截图）

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

apt install net-tools network-manager openssh-server

apt install network-manager

apt install openssh-server

退出系统

9.到进入b系统（10分）（并贴图）

sudo reboot

ubuntu 123456 （截图）

10.到获取永久ip完（10分）（并贴图）

bash

sudo vim /usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf

sudo systemctl restart NetworkManager

ip a （截图）

sudo apt update

11.安装图形化界面后安装salt-minion完（10分）（并贴图）

sudo apt install tasksel

sudo tasksel

空格选中 tab ok

ubuntu desktop (截图）

sudo apt install open-vm-tools (充满)

salt-minion

sudo apt update

sudo apt upgrade

sudo apt install salt-minion

sudo vim /etc/salt/minion

master: tecxz.com

使用文本编辑器按a改#master：salt，

将#删除由蓝色变成白色后将salt改为master：tecxz.com,

之后按esc退出编辑模式按：wq

sudo vim /etc/salt/minion_id

sudo systemctl restart salt-minion

sudo systemctl status salt-minion

sudo systemctl enable salt-minion

（自己学号，截图）

12.安装搜狗到配置并生成字符集完（5分）

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

apt search chinese

vim /etc/enviroment

空一格 加上

LANG=CN

LANGUAGE=zh_cn

LC_CTYPE=“zh_cn.UTF-8"

重启（截图）

安装WPS到更新用户的字体完（5分）（并贴图）

浏览器输入 bing WPS wps Office -Free Office Downloads for pc 进去

右上角Downloads deb

将位置改为桌面

cd Download

sudo dpkg -i wps（补全）

点击Activities

搜索wps（一行代表成功）

进入WPS会要求同意一个协议

web.tecxz.com:9080

file

weixin

wps

unzip wps-fonts.zip

ls /usr/share/fonts

sudo mv wps-fonts-master/wps/ /usr/share/fonts/wps-fonts

fc-cache -fv （截图）

重启

14.安装微信完（5分）（并贴图）

cd Download

sud0 dpkg -i wei（补全）（截图）

15.安装远程桌面完并能用Windows的远程桌面连接（5分）（并贴图）

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

ubuntu 123456 (截图)

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

10.重启以后并打开终端：zsh （截图）

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
