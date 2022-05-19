考试 UEFI一定

旧的里面装 jammy那个镜像

选项 高级 UEFI

install 第三个

MobaXterm

阿里云

浏览器 bing.com ubuntu sources.list ustc

其中，gg为跳转到文件首行；dG为删除光标所在行以及其下所有行的内容；

再细讲，d为删除，G为跳转到文件末尾行；

sudo gedit /etc/apt/sources.list

sudo apt update

sudo apt upgrade

sudo apt install openssh-server

sudo systemctl restart sshd

sudo systemctl status sshd

sudo systemctl enable sshd

ssh ubuntu@localhost yes

exit加回车退回正确系统

ssh ubuntu@localhost

ctrl加D退回之前系统

MobaXterm Session ssh host（IP a地址） 打钩 ubuntu 22 OK r

重新启动 必须 yes cancel

whoaim 用户名

lsblk

设置 添加 硬盘（第一个） scsl 存储save 确定 sudo reboot

sudo apt install gdisk

sudo gdisk /dev/sdb o y p s n 回车 回车 （last sector）+512M

(Hex 8300) ef00 n 回车回车回车 p s w y

sudo gdisk /dev/sdb p s c 1 syzesp c 2 syroot w y

y 修改别名n

sudo gdisk /dev/sdb p w y

格式化 sudo mkfs.vfat --help

sudo mkfs.vfat -F32 /dev/sdb1

sudo mkfs.ext4 /dev/sdb2 y

sudo mkdir /mnt/usb 创建一个新目录 ( sudo rm -r /mnt/usb删除）

sudo mount /dev/sdb2 /mnt/usb （mount挂载）

sudo mkdir /mnt/usb/boot/efi -p（目录不可以多次创建，除非用-p） （sudo mkdir -p /mnt/usb/boot/efi ）

sudo mount /dev/sdb1 /mnt/usb/boot/efi/

sudo apt install debootstrap

sudo debootstrap --arch=amd64 focal /mnt/usb/ https://mirrors.ustc.edu.cn/ubuntu/

sudo apt install arch-install-scripts

sudo mount -o bind /dev/ /mnt/usb/dev/

sudo mount -o bind /proc/ /mnt/usb/proc/

sudo mount -o bind /sys/ /mnt/usb/sys/ （一定要先改回去）

sudo cp /etc/apt/sources.list /mnt/usb/etc/apt/

(sudo apt install emacs)

sudo vim /etc/apt /sources.list

jammy变成focal

sudo genfstab -U /mnt/usb/ > /mnt/usb/tmp/fstab

（ls /mnt/usb/

ls /mnt/usb/dev/

ls /mnt/usb/proc/

ls /mnt/usb/sys/

lsblk）

sudo chroot /mnt/usb/ /bin/bash

mv /tmp/fstab /etc/fstab

apt update

apt install linux-image-generic 第二项

useradd ubuntu -m

ls /home/

passwd root （passwd）

passwd ubuntu

apt install vim

visudo Men admin改成ubuntu ALL %不变 （大写）

apt install efibootmgr

apt install grub-efi-amd64

mount -t efivarfs efivarfs /sys/firmware/efi/efivars/

grub-install -v --target=x86_64-efi --recheck /dev/sdb

sudo apt vim

vim /etc/default/grub 白色倒二加个#

update-grub

apt install net-tools network-manager openssh-server

apt install network-manager

apt install openssh-server

退出系统

sudo reboot

ubuntu 123456

chsh -s /bin/bash

退出重新进

sudo vim /usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf

俩行删除

sudo systemctl restart NetworkManager

ip a

sudo apt update

(设置 原来（第一个）移除 确定 摘除 重启 reboot)

（sudo gedit /etc/apt/sources.list检查源，如果不是及时更换，如果已经装，卸载重新安装）

sudo apt install tasksel

sudo tasksel

ubuntu desktop

（sudo tasksel install ubuntu-desktop sudo apt install ubuntu-gnome-desktop) ubuntu desktop 安装好重启，屏幕两边是黑的 (sudo apt install xterm ok)

sudo apt install open-vm-tools (充满)

登入mox

date 系统时间

timedatectl

sudo timedatectl set-timezone Asia/Shanghai (CST当地时间)

sudo dpkg-reconfigure locales (支持的语言)

en_us ISO-1 (前两个)

en_us ISO -15

第三个 en_us

zh-CN 打开 四个

输入法

sogou for liux x86

cd Downloads/

ll 五、搜狗输入法 sougou for liux

sudo apt update && sudo apt dist-upgrade -y

sudo dpkg -i sogoupinyin_4.0.0.1605_amd64.deb

sudo apt install -f -y

sudo dpkg -i sogoupinyin_4.0.0.1605_amd64.deb

sudo apt remove --purge ibus* -y

sudo apt install libqt5qml5 libqt5quick5 libqt5quickwidgets5 qml-module-qtquick2

sudo apt install libgsettings-qt1

sudo reboot

方块 co 加号 最低上 sogou 重启

vim .xprofile

普通用户

export XMODIFIERS="@im=fcitx"

export XIM="fcitx"

export XIM_PROGRAM="fcitx"

fcitx &

log out

(不让输入 sudo locale-gen

locale sudo vim /etc/environment

下面加上

LANG=CN

LANGUAGE=ZH-CN

LC_CTYPE=“zh_CN”

重启）

浏览器输入 bing WPS Office -Free Office Downloads for pc 进去

右上角Downloads deb

(apt search wps_office

free Download

wps office ）

cd Downloads/

ll

sudo dpkg -i

acti wps2019 打钩 con

Docu

vim .xprofile

普通用户

export XMODIFIERS="@im=fcitx"

export XIM="fcitx"

export XIM_PROGRAM="fcitx"

export GTK_IM_MODULE="fcitx"

export QT_IM_MODULE="fcitx"

fcitx &

重启

web.tecxz.com:9080

file

weixin

wps

cd Downloads/

ll

unzip wps-fonts.zip

ls /usr/share/fonts

sudo mv wps-fonts-master/wps/ /usr/share/fonts/wps-fonts

fc-cache -fv

log out

cd Downloads/

ll

sudo dpkg -i

远程桌面

sudo apt install xrdp

sudo systemctl restart xrdp

sudo systemctl status xrdp

sudo systemctl enable xrdp

sudo usermod -aG ssl-cert xrdp

sudo vim /ect/xrdp/startwm.sh

蓝色下面 在if test -r 上面添加

Unset DBUS_SESSION_ADDRESS

Unset XDG_RUNTIME_DIR

:wq

sudo systemctl restart xrdp

log out

用windows的远程桌面连接 输入ubuntu的ip 弹出大框点是

进入后输入用户名 ubuntu 密码 (旧的不进去）

重启

开机狂按 esc

reboot

安装zsh

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

10.重启以后并打开终端：

三 搜狗输入法

chsh -s /bin/bash log out

chsh -s /bin/bash/zsh log out 俩次

四 克隆 zsh

git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions （热点）

vim ~/.zshrc

plugins=(git zsh-autosuggestions)

source ~/.zshrc

六 sudo apt update && sudo apt upgrade

sudo apt install salt-minion

sudo vim /etc/salt/minion master: tecxz.com

sudo vim /etc/salt/minion_id

sudo systemctl restart salt-minion

sudo systemctl status salt-minion

https://note.youdao.com/s/2CMsxwMW

下载samba

安装和配置samba

1.安装samba：sudo apt install samba

2.创建用户:sudo useradd share

3.设置samba口令:sudo smbpasswd -a share

4.建立目录用来存放文件:sudo mkdir /data

5.用用户名目标文件:sudo chown share.share /data

6.删除一个文件:sudo rm /etc/samba/smb.conf

7.打开浏览器搜索http://tecxz.com:9090/class/ smb.conf save link as

8.用vim打开文件:vim smb.conf,查看是否有问题，若无问题则退出

9.将文件移动到samba目录下:sudo mv smb.conf /etc/samba

10.重启服务:sudo systemctl restart smbd.service

11.查看服务状态:sudo systemctl status smbd.service

12.查看当前IP:ip a

13.使smb开机自启:sudo systemctl enable smbd.service

14.在windows中在此电脑中访问ip a //

share 123456

16.将ubuntu中的文件复制到次文件夹中:

sudo cp ../Downloads/sogou /data

17.然后去windows上的文件夹中查看

下载salt-minion

1.安装salt-minion:

sudo apt install salt-minion

2.先进入文本：

sudo vim /etc/salt/minion

3.使用文本编辑器按a改#master：salt，将#删除由蓝色变成白色后将salt改为master：tecxz.com,之后按esc退出编辑模式按：wq

4.启动salt-minion：

sudo systemctl start salt-minion

5.查看状态：

sudo systemctl status salt-minion

7.然后使其开机自启：

sudo systemctl enable salt-minion
