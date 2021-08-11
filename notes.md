### 技巧

- ```sh
  alias tt='gio trash'  ~/.bashrc  用于替换rm -rf 的操作 会到回收箱进行回收
  ```

- 查看系统版本 `cat /etc/kylin-build`

- 查看系统的      file  /bin/ls

- 添加自己的PPA 

  ```
  [trusted=yes]  在source.list增加
  ```

- ```ssh
  aptitude download <package_name> 下载指定的安装包
  ```

- ```cpp
  qDebug() << "Ax" << "[" << __func__ << ":" << __TIME__ << "]";
  ```

- ```sh
  sudo vi /etc/dpkg/dpkg.cfg  no-debsig  解决包安装不上的情况
  ```

- 必要的依赖

  ```sh
  编包需要的库 sudo apt install debhelper devscripts automake dh-make build-essential -y 
  
  ```

- apt

  ```
  sudo apt install ukui-kwin = 版本 安装指定的版本
  apt-cache policy <package name> will show the version details
  
  ```

#### 设备信息

```sh
一、主机ip信息如下:
	主机ip:172.17.129.112
二、磁盘信息如下:
	该服务器共有
	磁盘:/dev/sr0 的序列号为:476021509361
	磁盘:/dev/nvme0n1 的序列号为:50026B7683B97FB4
三、内存信息如下:
	系统总内存为:8078480 KB
	系统当前可用内存为:6119256 KB
	系统交换空间总内存为:9692156 KB
	系统交换空间当前可用内存为:9692156 KB
四、CPU信息如下:
	 CPU的厂商,编号,主频为: Phytium,FT-2000/4
	该服务器共有
	每个物理CPU内核个数:
hostinfo_check1_1.sh:49: no matches found: /etc/sysconfig/network-scripts/ifcfg-*
log:1: 权限不够: /var/log/hostinfo_check.log
hostinfo_check1_1.sh:54: no matches found: /etc/sysconfig/network-scripts/ifcfg-*
四、网卡信息如下:
	该服务器共配置网卡:
五、网卡mac地址信息如下:
	网卡:enaftgm1i0 的mac地址为:3c:6a:2c:bf:98:80
	网卡:sit0 的mac地址为:00:00:00:00
	网卡:lo 的mac地址为:00:00:00:00:00:00
	网卡:ip6tnl0 的mac地址为:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00
```




### Dkpg

- 实例

  ```sh
  dpkg -i package.deb     #安装包
  dpkg -r package         #删除包
  dpkg -P package         #删除包（包括配置文件）
  dpkg -L package         #列出与该包关联的文件
  dpkg -l package         #显示该包的版本
  dpkg --unpack package.deb  #解开deb包的内容
  dpkg -S keyword            #搜索所属的包内容
  dpkg -l                    #列出当前已安装的包
  dpkg -c package.deb        #列出deb包的内容
  dpkg --configure package   #配置包
  ```

- 查找依赖

  ```shell
  objdump -p bin | grep NEEDED 手动查找某个可执行文件的依赖
  
  ```


### git 教程

- git

  ```shell
  git config --global alias.co checkout
  git config --global alias.br branch
  git config --global alias.ci commit
  git config --global alias.st status
  git config --global alias.unstage 'reset HEAD --'
  git config --global alias.last 'log -1 HEAD'
  git config --global alias.logl 'log --oneline'
  ```

  

- ##### Git 全局设置

  ```shell
  git config --global user.name "wa"
  git config --global user.email "wangsong@kylinos.cn"
  ```

- ##### 创建一个新仓库

  ```shell
  git clone http://172.17.66.163/wangsong/libkysset-1.1kord.git
  cd libkysset-1.1kord
  touch README.md
  git add README.md
  git commit -m "add README"
  git push -u origin master
  ```

- ##### 推送现有文件夹

  ```shell
  cd existing_folder
  git init
  git remote add origin http://172.17.66.163/wangsong/libkysset-1.1kord.git
  git add .
  git commit -m "Initial commit"
  git push -u origin master
  ```

- ##### 推送现有的 Git 仓库

  ```shell
  cd existing_repo
  git remote rename origin old-origin
  git remote add origin http://172.17.66.163/wangsong/libkysset-1.1kord.git
  git push -u origin --all
  git push -u origin --tags
  
  ```

- git branch -D/-d branch_2 删除本地的分支 -D没有合并也可以删除 -d不会

- git pull origin develop 确保主分支为最新的版本

- git checkout -b feat-1 常见一个叫feat-1的分支并切换过去

- git rebase -i HEAD~3 合并commit message信息 

- git push origin feat-1 把本地的仓库 推送到远程当中

- git pull --rebase origin develop 将远程的主分支以rebase的方式合并到当前的分支

- git cherry-pick **c843c37**  将分支的对应代码合并到当前的分支中

- git clone -b +分支 + 地址 克隆指定分支的远程

- git reset --hard dbb15d2 版本回退


### 打印

- qDebug() << "axel:: gogogogogo";

- http://172.17.66.192.kylin.com/biz/productplan-view-433-bug-id_desc.html

### SSH密匙

```sh
ssh-keygen -t rsa -C "wangsong@kylinos.cn"

cat /home/lxy/.ssh/id_rsa.pub

windows cat C:/Users/Axel/.ssh/id_rsa.pub
```

### samba

```
sudo apt install samba 
sudo smbpasswd -a $USERNAM
sudo service smbd restart
```

### zsh

```
sudo apt install zsh -y;

wget https://gitee.com/mirrors/oh-my-zsh/raw/master/tools/install.sh;

chmod +x install.sh;
./install.sh;

cd ~/.oh-my-zsh/custom/plugins;

git clone https://github.com/zsh-users/zsh-syntax-highlighting;
```

### 清华源

```sh
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse
```

```sh
#是否是能log日志跟踪
if [ $OPEN_SCP ];then
	#传输各种脚本到设备中
	spawn scp -r ./atuo_itp $username@$realip:/home/kylin/桌面/test

	expect {
			"yes/no" { send "yes\r"; exp_continue }
			"password" { send "$password\r" };
	}
fi
```





### 编译条件

- cmake添加-g 在文件 CMakeLists.txt添加下面一条语句 add_definitions("-Wall -g")
- QMAKE_CXXFLAGS += -g



### Go

- 下载：https://golang.org/doc/install

- 安装：tar -C /usr/local -xzf go1.16.6.linux-arm64.tar.gz

- 环境变量

  ```shell
  export GOROOT=/usr/local/go
  export GOBIN=$GOROOT/bin
  export PATH=$PATH:$GOBIN
  export GOPATH=$HOME/share/Go
  export GOPROXY=https://goproxy.cn
  ```



### OTA

- v10 SP1服务器代码：https://dev.kylin.com/kylin-desktop/v101/+source/kylin-sourceinfo-server

- v10 SP1客户端：https://dev.kylinos.cn/kylin-desktop/+source/kylin-update-manager/5.7.1kordhw1

- V10客户端:https://dev.kylinos.cn/kylinos-desktop/v100/+source/kylin-update-manager

- V10-PPA:dput dev:kylinos-desktop/v100-proposed

-  基础操作

  ```shell
  重启服务：sudo service mysql restart && sudo systemctl restart kylin-sourceinfo-server
  修改服务器地址：sudo vi /var/lib/kylin-software-properties/template/kylin-source-update.conf
  
  测试：curl http://localhost:59546/client/45984185811f-8898ada3c94eb62f3089abf0389e13f2/
  curl http://localhost:5600/api/0/buckets/
  
  ```
  
- 源管理器服务端主要用于更新源信息与源管理器客户端相互通信 进行修改源信息

- 条件：

  如果是最新的v10版本，可以修改/var/lib/kylin-software-properties/template/important.list 里面加一个包名比如，kylin-video，然后sudo chattr +i /var/lib/kylin-software-properties/template/important.list  然后apt remove kylin-video 再打开就可以检测到更新

- 



### source

```sh
deb http://archive.kylinos.cn/kylin/KYLIN-ALL .test-10.1 main restricted universe multiverse
deb http://archive.kylinos.cn/kylin/partner 10.1 main
deb http://archive2.kylinos.cn/deb/kylin/production/PART-V10-SP1/custom/partner/V10-SP1 default all

172.20.191.4 archive.launchpad.dev answers.dev.kylin.com archive.dev.kylin.com api.dev.kylin.com bazaar.dev.kyli
n.com bazaar-internal.dev.kylin.com blueprints.dev.kylin.com bugs.dev.kylin.com code.dev.kylin.com feeds.dev.kyl
in.com lists.dev.kylin.com ppa.dev.kylin.com private-ppa.dev.kylin.com translations.dev.kylin.com xmlrpc-private
.dev.kylin.com xmlrpc.dev.kylin.com dev.kylin.com testopenid.dev ppa.launchpad.dev
172.20.191.4 keyserver.dev.kylin.com
172.20.191.3 builder.kylin.com
172.20.191.29 oauth.kylin.com
172.20.191.22 zsk.kylin.com
172.17.66.61 zentao.tjsource.xyz zentao.kylin.com
```



### 监控

- https://github.com/ActivityWatch/activitywatch

- ```sh
  sudo apt install nodejs -y && sudo apt install npm -y && sudo apt install python3-pip
  ```



ERROR: launchpadlib 1.10.13 requires testresources, which is not installed.

### Wayland

协议文档：https://wayland.app/protocols/



  MACs hmac-sha2-512

  User kylin

  IdentityFile "C:\Users\Axel\.ssh\id_rsa"



get_app_changelog



app_msg["version"] app_msg.CANDIDATEVERSION

app_msg["installversion"] app_msg.INSTALLEDVERSION



