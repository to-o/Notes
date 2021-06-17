```sh
route add 0.0.0.0 mask 0.0.0.0 10.23.0.1

route add 172.17.0.0 mask 255.0.0.0 172.17.5.253

route delete 0.0.0.0 -p
route delete 172.17.0.0 -p
route delete 172.20.0.0 -p

route add 0.0.0.0 mask 0.0.0.0 172.17.5.253

route add 0.0.0.0 mask 0.0.0.0 192.168.17.255

route add 172.20.0.0 mask 255.255.0.0 172.17.5.253
route add 172.17.0.0 mask 255.255.0.0 172.17.5.253

https://blog.csdn.net/liyu1059915776/article/details/90237910
https://blog.csdn.net/mochou111/article/details/90749598
```

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





dpkg-source  --commit

### dh_translations --domain

fdfdfdsfd



```
journalctl -f -u NetworkManager

 nmcli general logging level TRACE domains ALL
```

```
sudo apt install pkg-config intltool libglib2.0-dev ppp-dev libpolkit-gobject-1-dev libpolkit-agent-1-dev libselinux1-dev libaudit-dev libgnutls28-dev  uuid-dev libsystemd-dev libudev-dev libgirepository1.0-dev gobject-introspection libpsl-dev libcurl4-gnutls-dev gtk-doc-tools libyaml-perl libglib2.0-doc libmm-glib-dev   libndp-dev libreadline-dev libnewt-dev  libteam-dev valac libbluetooth-dev libjansson-dev libnss3-dev -y
```

```
   36  ls
   37  dpkg-source -x network-manager_1.22.10-1kylin1hw16.dsc 
   38  ls
   39  cd network-manager-1.22.10/
   40  ./configure 
   41  debuild
   42  cd ..
   43  ls
   44  cd network-manager-1.22.10/
   45  ls
   46  cd ..
   47  ls
   48  cd ..
   49  ls
   50  sudo rm -rf network-manager/
   51  ls
   52  cd network-manager/
   53  dpkg-source -x network-manager_1.22.10-1kylin1hw16.dsc 
   54  ls
   55  cd network-manager-1.22.10/
   56  ls
   57  meson build
   58  sudo apt install meson 
   59  sudo apt install camke 
   60  sudo apt install cmake 
   61  ls
   62  meson build
   63  sudo apt install build-essential libdbus-glib-1-dev libgirepository1.0-dev
   64  meson build
   65  sudo apt install mobile-broadband-provider-info
   66  meson build
   67  cmake 
   68  ls
   69  meson build
   70  sudo apt install qtcore
   71  sudo apt install qtcore4-l10n 
   72  meson build
   73  meson buil
   74  sudo apt install libqtcore4
   75  meson buil
   76  sudo apt install libqtcore4
   77  sudo apt install libqt4-core
   78  sudo apt-get install qt4-dev-tools
   79  meson build
   80  ls
   81  cd buil
   82  cd ..
   83  meson build
   84  cd build
   85  ls
   86  najia
   87  ninja 
   88  history 

```

```
sudo apt install meson qt4-dev-tools build-essential libdbus-glib-1-dev libgirepository1.0-dev mobile-broadband-provider-info
```

 252 x 123qwe

213 x qwe123

111 



ITP测试

| 开始时间        | 结束时间     | 测试台数 | 奔溃数 | 备注 |
| :-------------- | ------------ | -------- | ------ | ---- |
| 6月12号17点30分 | 6月15号8点30 | 3        | 0      |      |
| 6/16 21.00      | 6/17 9.00    | 3        | 0      |      |
|                 |              |          |        |      |

