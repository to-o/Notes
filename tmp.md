

### KWIN

- 日志：https://docs.qq.com/sheet/DTnVVSExJWU9Ja3hZ?tab=BB08J2   请大家再根据最新组件情况更新下日志信息
- 



1. 何承原同事是一个积极上进的人，在本次海南攻关项目中他做事踏实，不怕苦，长期的加班攻关中没有说过放弃一直坚持完成自己的任务。
2. 何承原同事在完成项目时，思路清晰，目标明确，而且在我们遇到困难时以主动参与解决，对我们项目的进度提高都作出了很大的贡献。
3. 何承原同事在生活上也给予我很大的帮助，帮助我解决生活中的一些困难，每次找何承员同事他都很热心的前来帮助解决所以我推荐他成为一位优秀的共产党员
4. 何承原同事也积极的组织各项活动，团结同事丰富我们的文化娱乐，我认为该同志从思想上、行动上都积极的向党靠拢，已经具备成为一位党员的条件

- 
- 





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

```

```

ITP测试

| 开始时间    | 结束时间  | 测试台数 | 奔溃数 | 备注 |
| :---------- | --------- | -------- | ------ | ---- |
| 6/12/ 17.30 | 6/15 8.30 | 3        | 0      |      |
| 6/16 21.00  | 6/17 9.00 | 3        | 0      |      |
|             |           |          |        |      |



- wifi 相同的IP 配置DNS时 也不生效





