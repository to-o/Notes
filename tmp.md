 	

### KWIN

- 日志：https://docs.qq.com/sheet/DTnVVSExJWU9Ja3hZ?tab=BB08J2   请大家再根据最新组件情况更新下日志信息

  172.17.50.10





```sh

sudo apt install breeze-dev cmake debhelper extra-cmake-modules kinit-dev kscreenlocker-dev libcap-dev libdrm-dev libegl1-mesa-dev libepoxy-dev libfontconfig1-dev libfreetype6-dev  libice-dev libinput-dev libkdecorations2-dev libkf5activities-dev libkf5completion-dev libkf5config-dev libkf5configwidgets-dev libkf5coreaddons-dev libkf5crash-dev libkf5declarative-dev libkf5doctools-dev libkf5globalaccel-dev libkf5i18n-dev libkf5iconthemes-dev libkf5idletime-dev libkf5kcmutils-dev libkf5kio-dev libkf5newstuff-dev libkf5notifications-dev  libkf5package-dev libkf5plasma-dev libkf5service-dev libkf5textwidgets-dev libkf5widgetsaddons-dev libkf5windowsystem-dev libkf5xmlgui-dev libqt5sensors5-dev libqt5x11extras5-dev libsm-dev libudev-dev libwayland-dev libx11-xcb-dev libxcb-composite0-dev libxcb-cursor-dev libxcb-damage0-dev libxcb-glx0-dev libxcb-icccm4-dev libxcb-image0-dev libxcb-keysyms1-dev libxcb-randr0-dev libxcb-render0-dev libxcb-shape0-dev libxcb-shm0-dev libxcb-sync-dev libxcb-util-dev libxcb-xfixes0-dev libxcb-xtest0-dev libxcb1-dev libxcursor-dev libxi-dev libxkbcommon-dev pkg-config pkg-kde-tools qtbase5-dev qtbase5-private-dev qtdeclarative5-dev qtscript5-dev qttools5-dev libgsettings-qt-dev kwin-dev libgbm-dev  libkf5wayland-dev
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



出现问题的原因是区域更新中damage region计算错误，现已修复这个问题。

测试建议：

多种情形下反复测试，类似的闪屏问题都和damage 计算相关。

影响区域：

显示闪烁，或导致鼠标移动出现轨迹。



单元测试】通过
【硬件环境】9A0笔记本
【软件环境】0628版本ISO





### 周报





  QPoint cur = QCursor::pos();



  int cx = cur.x()+10;

  int cy = cur.y()+10;

  QCursor::setPos(cx,cy);











