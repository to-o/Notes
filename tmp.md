 	

### KWIN

- 日志：https://docs.qq.com/sheet/DTnVVSExJWU9Ja3hZ?tab=BB08J2   请大家再根据最新组件情况更新下日志信息

  172.17.50.10





```sh

sudo apt install breeze-dev cmake debhelper extra-cmake-modules kinit-dev kscreenlocker-dev libcap-dev libdrm-dev libegl1-mesa-dev libepoxy-dev libfontconfig1-dev libfreetype6-dev  libice-dev libinput-dev libkdecorations2-dev libkf5activities-dev libkf5completion-dev libkf5config-dev libkf5configwidgets-dev libkf5coreaddons-dev libkf5crash-dev libkf5declarative-dev libkf5doctools-dev libkf5globalaccel-dev libkf5i18n-dev libkf5iconthemes-dev libkf5idletime-dev libkf5kcmutils-dev libkf5kio-dev libkf5newstuff-dev libkf5notifications-dev  libkf5package-dev libkf5plasma-dev libkf5service-dev libkf5textwidgets-dev libkf5widgetsaddons-dev libkf5windowsystem-dev libkf5xmlgui-dev libqt5sensors5-dev libqt5x11extras5-dev libsm-dev libudev-dev libwayland-dev libx11-xcb-dev libxcb-composite0-dev libxcb-cursor-dev libxcb-damage0-dev libxcb-glx0-dev libxcb-icccm4-dev libxcb-image0-dev libxcb-keysyms1-dev libxcb-randr0-dev libxcb-render0-dev libxcb-shape0-dev libxcb-shm0-dev libxcb-sync-dev libxcb-util-dev libxcb-xfixes0-dev libxcb-xtest0-dev libxcb1-dev libxcursor-dev libxi-dev libxkbcommon-dev pkg-config pkg-kde-tools qtbase5-dev qtbase5-private-dev qtdeclarative5-dev qtscript5-dev qttools5-dev libgsettings-qt-dev  libkf5wayland-dev

kwin-dev libgbm-dev 
```



```
【990地址】
系列代号定为 v101.hw，对应版本号10.1.hw，changelog写v101.hw
版本系列地址：
https://launchpad.dev/kylin-desktop/v101.hw
源码包查看地址：
https://launchpad.dev/+kylin/archive_publish?distro=kylin-desktop&series=v101.hw
上传源码: 
dput dev:kylin-desktop/v101.hw-proposed xxxx_source.changes

【9006C】
系列代号定为 v101.hw，对应版本号10.1.hw，changelog写v101.hw
版本系列地址：
 https://launchpad.dev/kylin-desktop-kv/v101.hw
源码包查看地址：
https://launchpad.dev/+kylin/archive_publish?distro=kylin-desktop-kv&series=v101.hw
上传源码: dput dev:kylin-desktop-kv/v101.hw-proposed xxxx_source.changes


```





```
使用990专业内网源
deb http://archive.launchpad.dev/kylin v101 main restricted universe multiverse
deb http://archive.launchpad.dev/kylin-desktop v101.hw main restricted universe multiverse
deb http://archive.launchpad.dev/kylin-desktop v101.hw-updates main restricted universe multiverse
deb http://archive.launchpad.dev/kylin-desktop v101.hw-proposed main restricted universe multiverse


172.20.191.4    archive.kylinos.cn launchpad.dev answers.launchpad.dev archive.launchpad.dev api.launchpad.dev bazaar.launchpad.dev bazaar-internal.launchpad.dev blueprints.launchpad.dev bugs.launchpad.dev code.launchpad.dev feeds.launchpad.dev keyserver.launchpad.dev lists.launchpad.dev ppa.launchpad.dev private-ppa.launchpad.dev testopenid.dev translations.launchpad.dev xmlrpc-private.launchpad.dev xmlrpc.launchpad.dev

```



```
journalctl -f -u NetworkManager

 nmcli general logging level TRACE domains ALL
```

```
sudo apt install pkg-config intltool libglib2.0-dev ppp-dev libpolkit-gobject-1-dev libpolkit-agent-1-dev libselinux1-dev libaudit-dev libgnutls28-dev  uuid-dev libsystemd-dev libudev-dev libgirepository1.0-dev gobject-introspection libpsl-dev libcurl4-gnutls-dev gtk-doc-tools libyaml-perl libglib2.0-doc libmm-glib-dev   libndp-dev libreadline-dev libnewt-dev  libteam-dev valac libbluetooth-dev libjansson-dev libnss3-dev -y
```



### OTA

- https://dev.kylin.com/kylin-desktop/v101/+source/kylin-sourceinfo-server

Map cursors from X11 to Wayland

Tracking cursor changes in X11. Whenever the cursor image changes, the
image is read and a wl_buffer is created with the content of the X11
cursor. This buffer is attached to a surface used as a cursor image.

As a memory pool for the cursor buffers a temporary file is created and
mmapped.

All created cursors are cached but not yet removed from the cache. Some
cleanup code would be useful also to ensure that our shared memory pool
doesn't overflow.



```export PATH=$PATH:/usr/local/go/bin
export PATH=$PATH:/usr/local/go/bin
```

40cb4f5cd Map cursors from X11 to Wayland



### Dbus

1. Bus Name 总线名称（com.myconpany.Test）连接到dbus会给与分配，但是为了好记采用绑定的方式
2. 对象路径（/com/mytest）路径名称的Dbus的应用程序都包含一些对象，当接收到一条消息的时候发给的一个对象不是整个程序，这个在整个会话中也是唯一的
3. 接口（org.freedwsktop.test）每个对象有一个或多个接口，接口时一组方法和信号
4. 方法和信号 方法就是一个函数代码有输入和输出，信号是一种广播，dbus有四种类型的消息：方法调用、方法返回、信号、错误

```c
Address –> [Bus Name] –> Path –> Interface –> Method
```



代码执行路径

- 创建一个System D-bus的连接
- 进行连接判断 是否连接上 设置连接超时、连接次数判断等操作
- 注册过滤器 过滤器是对所有传入的信息运行的处理程序（dbus服务最关键的一个函数，它处理输入队列分发的所有消息。判断消息是否合法以及是否有注册的上层用户的handler来处理 ）
- 设置BUS name：test.wei.dest
- 服务启动就开始计算生命周期 增加失败计数和失败的计数
- 异步任务队列 `进程`模式和`线程`模式处理消息（同时增加信号的处理 包括子进程的回收机制）
- 注册DBUS接口 (使用xml定义D-Bus接口)在D-Bus中，可以将D-Bus接口定义用XML格式表述处理，并利用工具，自动生成头文件，给出工整的调用方式。
- 注册DBUS信号



之后的处理过程

- 建立一个D-bus
- 动态加载动态连接库
- 注册自己的包Dbus的方法
- 事件循环
- 





```
sudo apt install qtpositioning5-dev qtpositioning5-dev 
```













