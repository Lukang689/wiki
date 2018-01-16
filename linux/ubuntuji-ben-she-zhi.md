### 基础软件安装

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install vim eclipse eclipse-cdt meld bless subversion git rabbitvcs-* python3-dev python3-pyqt5 python3-pip manpages-dev manpages-posix-dev chromium-browser ksnapshot nginx mysql-server mysql-client php ctags php-fpm subversion mysql-workbench rar unrar build-essential automake autoconf libtool php php-mysql php-fpm php-ssh2
```

### 常用命令

##### 删除当前目录下的所有.svn文件

```
find . -type d -name ".svn"|xargs rm -rf
```

##### 删除当前目录下除 _.iso 和 _.zip 外的所有文件

```
find . -type f -not \(-name '*.zip' -or -name '*.iso' \) -delete
```

##### 修改MAC地址

```
sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:AA:BB:CC:DD:EE
sudo ifconfig eht0 up
```

##### 修改时区

```
sudo timedatectl set-timezone "Asia/Shanghai"
```

##### wps无法使用搜狗输入法解决办法

编辑/usr/bin/下的wps,wpp,et,添加语句

```
export XMODIFIERS="@im=fcitx"
export QT_IM_MODULE="fcitx"
```

##### ubuntu 16.04+安装openjdk7

```
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt-get update
sudo apt-get install openjdk-7-jdk
```

##### root用户开机自动登录

编辑/usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf,增加语句

```
autologin-user=root
greeter-show-manual-login=true
```

##### ubuntu出现broken package?

在/var/lib/dpkg/status文件中找到相应的包，删除对应的代码段

### GCC编译器

##### 去除所有警告

```
-w
```

##### 静态库循环链接

```
mipsel-linux-gcc main.c libirdetoca.so -Xlinker "-(" s3_dvb_client_3.14.4.lib xc_wb.a libljsysinfo.a CloakedCAAgent.lib -Xlinker "-)"
```

##### ssh登录运行shell，ssh退出脚本继续运行

```
ctrl + z 停下来，这里有个id，一般是1
bg 1
disown -h %1
```

### 更改IGMP版本号

```
su
cat /proc/sys/net/ipv4/conf/eth0/force_igmp_version
echo "2" > /proc/sys/net/ipv4/conf/eth0/force_igmp_version
```

### windows--&gt;linux格式转换

用vi打开，执行

```
:set ff=unix
```

### tar打包压缩

    tar czvf test.tar.gz `ls -A`

### 加入组播组路由

```
route add -net 224.0.0.0 netmask 224.0.0.0 enp4s0
route add -net 0.0.0.0 netmask 0.0.0.0 enp4s0
```

### NFS挂载

服务器端配置

```
sudo apt-get install nfs-kernel-server
```

编辑/etc/exports

```
/home/djstava *(rw,sync,no_root_squash,no_subtree_check)
```

客户端挂载

```
sudo apt-get install nfs-common
sudo mount -t nfs 10.0.0.166:/home/longjing /mnt
```

### ssh非22端口登录

```
ssh -p 2666 root@10.0.0.210
```

### scp使用非22端口

```
scp -P 26666 file 10.0.0.210:/home/djstava/
```

### 多网卡vlc播放udp

```
vlc --miface eth0 udp://@225.0.0.100:9001
```

### ufw基本使用

```
sudo ufw enable/disable
sudo ufw allow 80
sudo ufw delete allow 80
```

### tar系统备份

```
su
cd /
tar cvpzf /media/djstava/backup.tgz --exclude=/proc --exclude=/media –exclude=/mnt –exclude=/sys
```

偶尔会出现"tar: Error exit delayed from previous errors", 将需要备份的目录都增加读的权限，另外备份还原系统时最好在live disk中进行

### samba基本使用

```
sudo apt-get install samba

# /etc/samba/smb.conf
[ubuntu]
    comment = ubuntu
    path = /home/xugaoxiang
    writable = yes
    valid user = xugaoxiang
    available = yes
    create mask = 0777
    directory mask = 0777
    public = yes
    
sudo /etc/init.d/smbd restart
```



