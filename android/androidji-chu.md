### adb远程抓图

```
adb shell /system/bin/screencap -p /data/android_traffic_balance_01.png
adb pull /data/android_traffic_balance_01.png .
```

### adb启动activity

#### 直接启动

```
adb shell am start -n com.xugaoxiang/com.xugaoxiang.MainActivity
```

#### 指定intent

```
adb shell am start -a intent_ACTION -c intent_category -n com.xugaoxiang/com.xugaoxiang.MainActivity
```

### 指定浏览器打开特定页面 ​​​​

```
am start -a android.intent.action.VIEW -d http://google.com
```

### 获取apk对应的包名和路径

```
adb shell pm list package -f
```

### 以读写方式重新挂载/system

```
mount -o remount,rw /system
```

### 关闭selinux

```
# 方法1
setenforce 0

# 方法2
echo 0 > /sys/fs/selinux/enforce

# 方法3
编辑BoardConfig.mk
BOARD_KERNEL_CMDLINE := console=ttyS0,115200n8 androidboot.hardware=zx2000 androidboot.serialno=01234567890123456789 androidboot.selinux=permissive
```

### 开机运行shell脚本

编辑init.$\(platform\).rc，增加

```
service makenode /system/etc/makebtusb0.sh
    class main
    user root
    group root 
    oneshot
```

makebtusb0.sh

```
#! /system/bin/sh

mknod /dev/btusb0 c 180 194
chmod 777 /dev/btusb0
```

### ADB操作特定设备

```
C:\Users\djstava>adb devices
List of devices attached
10.0.0.48:5555  offline
8D6TUCDI69D6G6AI        device
```

对某个设备进行操作

```
adb -s 8D6TUCDI69D6G6AI shell
```

### 修改MAC地址

```
su
netcfg(ifconfig) eth0 down
netcfg eth0 hwaddr 10:10:10:10:10:10
netcfg(ifconfig) eth0 up
```

### adb远程抓图

```
adb shell /system/bin/screencap -p /data/android_traffic_balance_01.png
adb pull /data/android_traffic_balance_01.png .
```

### adb启动activity

#### 直接启动

```
adb shell am start -n com.xugaoxiang/com.xugaoxiang.MainActivity
```

#### 指定intent

```
adb shell am start -a intent_ACTION -c intent_category -n com.xugaoxiang/com.xugaoxiang.MainActivity
```

### 指定浏览器打开特定页面 ​​​​

```
am start -a android.intent.action.VIEW -d http://google.com
```

### 获取apk对应的包名和路径

```
adb shell pm list package -f
```

### 以读写方式重新挂载/system

```
mount -o remount,rw /system
```

### 关闭selinux

```
# 方法1
setenforce 0

# 方法2
echo 0 > /sys/fs/selinux/enforce

# 方法3
编辑BoardConfig.mk
BOARD_KERNEL_CMDLINE := console=ttyS0,115200n8 androidboot.hardware=zx2000 androidboot.serialno=01234567890123456789 androidboot.selinux=permissive
```

### 开机运行shell脚本

编辑init.$\(platform\).rc，增加

```
service makenode /system/etc/makebtusb0.sh
    class main
    user root
    group root 
    oneshot
```

makebtusb0.sh

```
#! /system/bin/sh

mknod /dev/btusb0 c 180 194
chmod 777 /dev/btusb0
```

### ADB操作特定设备

```
C:\Users\djstava>adb devices
List of devices attached
10.0.0.48:5555  offline
8D6TUCDI69D6G6AI        device
```

对某个设备进行操作

```
adb -s 8D6TUCDI69D6G6AI shell
```

### 修改MAC地址

```
su
netcfg(ifconfig) eth0 down
netcfg eth0 hwaddr 10:10:10:10:10:10
netcfg(ifconfig) eth0 up
```

### adb远程抓图

```
adb shell /system/bin/screencap -p /data/android_traffic_balance_01.png
adb pull /data/android_traffic_balance_01.png .
```

### adb启动activity

#### 直接启动

```
adb shell am start -n com.xugaoxiang/com.xugaoxiang.MainActivity
```

#### 指定intent

```
adb shell am start -a intent_ACTION -c intent_category -n com.xugaoxiang/com.xugaoxiang.MainActivity
```

### 指定浏览器打开特定页面 ​​​​

```
am start -a android.intent.action.VIEW -d http://google.com
```

### 获取apk对应的包名和路径

```
adb shell pm list package -f
```

### 以读写方式重新挂载/system

```
mount -o remount,rw /system
```

### 关闭selinux

```
# 方法1
setenforce 0

# 方法2
echo 0 > /sys/fs/selinux/enforce

# 方法3
编辑BoardConfig.mk
BOARD_KERNEL_CMDLINE := console=ttyS0,115200n8 androidboot.hardware=zx2000 androidboot.serialno=01234567890123456789 androidboot.selinux=permissive
```

### 开机运行shell脚本

编辑init.$\(platform\).rc，增加

```
service makenode /system/etc/makebtusb0.sh
    class main
    user root
    group root 
    oneshot
```

makebtusb0.sh

```
#! /system/bin/sh

mknod /dev/btusb0 c 180 194
chmod 777 /dev/btusb0
```

### ADB操作特定设备

```
C:\Users\djstava>adb devices
List of devices attached
10.0.0.48:5555  offline
8D6TUCDI69D6G6AI        device
```

对某个设备进行操作

```
adb -s 8D6TUCDI69D6G6AI shell
```

### 修改MAC地址

```
su
netcfg(ifconfig) eth0 down
netcfg eth0 hwaddr 10:10:10:10:10:10
netcfg(ifconfig) eth0 up
```

### adb模拟键值发送

```
adb shell input keyevent $键值
```



