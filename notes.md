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
  git config --global user.name "王松"
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

cat /home/kylin/.ssh/id_rsa.pub

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

- 服务器代码：https://dev.kylin.com/kylin-desktop/v101/+source/kylin-sourceinfo-server

- 客户端：https://dev.kylinos.cn/kylin-desktop/+source/kylin-update-manager/5.7.1kordhw1

-  基础操作

  ```shell
  重启服务：sudo service mysql restart && sudo systemctl restart kylin-sourceinfo-server
  修改服务器地址：sudo vi /var/lib/kylin-software-properties/template/kylin-source-update.conf
  
  测试：curl http://localhost:59546/client/45984185811f-8898ada3c94eb62f3089abf0389e13f2/
  curl http://localhost:5600/api/0/buckets/
  
  ```
  
- 源管理器服务端主要用于更新源信息与源管理器客户端相互通信 进行修改源信息



### 监控

- https://github.com/ActivityWatch/activitywatch

- ```sh
  sudo apt install nodejs -y && sudo apt install npm -y && sudo apt install python3-pip
  ```



ERROR: launchpadlib 1.10.13 requires testresources, which is not installed.

### Wayland

协议文档：https://wayland.app/protocols/

















