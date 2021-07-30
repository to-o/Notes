#### 命令

```sh
UOS：/usr/bin/apt-get -d -o Debug::NoLocking=1 -c "/var/lib/lastore/apt_v2.conf" --print-uris --assume-no install tree

模拟：/usr/bin/apt-get -d -o Debug::NoLocking=1  --print-uris --assume-no install tree python

```



#### 参数说明

```sh
-d, --download-only
           Download only; package files are only retrieved, not unpacked or installed. Configuration Item: APT::Get::Download-Only.

-o, --option
       Set a Configuration Option; This will set an arbitrary configuration option. The syntax is -o Foo::Bar=bar.  -o and --option can be used
       multiple times to set different options.
       
-c, --config-file
           Configuration File; Specify a configuration file to use. The program will read the default configuration file and then this configuration file.
           If configuration settings need to be set before the default configuration files are parsed specify a file with the APT_CONFIG environment
           variable. See apt.conf(5) for syntax information.
 不是获取要安装的文件。       
--print-uris : instead of fetching the files to install, their URIs (links to download them) are printed. Each URI will have the path, the destination file name, the size and the expected md5 hash. Note that the file name to write to will not always match the file name on the remote site! This also works with the source and update commands. When used with the update command the MD5 and size are not included, and it is up to the user to decompress any compressed files. Configuration Item: APT::Get::Print-URIs.

--assume-no
           Automatic "no" to all prompts. Configuration Item: APT::Get::Assume-No.
           
--Debug::NoLocking disables all file locking. This can be used to run some operations (for instance, apt-get -s install) as a non-root user.
```



#### 测试用例

```sh
➜  ~ /usr/bin/apt-get -d -o Debug::NoLocking=1  --print-uris --assume-no install tree python   
正在读取软件包列表... 完成
正在分析软件包的依赖关系树       
正在读取状态信息... 完成       
注意，选中 'python-is-python2' 而非 'python'
下列软件包是自动安装的并且现在不需要了：
  cryptsetup cryptsetup-bin finalrd libyaml-cpp0.6 localechooser-data user-setup
使用'apt autoremove'来卸载它(它们)。
下列【新】软件包将被安装：
  python-is-python2 tree
升级了 0 个软件包，新安装了 2 个软件包，要卸载 0 个软件包，有 61 个软件包未被升级。
需要下载 45.1 kB 的归档。
解压缩后会消耗 121 kB 的额外空间。
'https://archive1.kylinos.cn/kylin/KYLIN-ALL/pool/main/w/what-is-python/python-is-python2_2.7.17-4_all.deb' python-is-python2_2.7.17-4_all.deb 2496 MD5Sum:6e0b9c818de5269a32052059ac02fb63
'https://archive1.kylinos.cn/kylin/KYLIN-ALL/pool/universe/t/tree/tree_1.8.0-1_arm64.deb' tree_1.8.0-1_arm64.deb 42608 MD5Sum:85cb5f72f4f56b60531871ac1e21b739

```



```json
[
 {deepin-elf-sign-tool elf签名工具 deepin-elf-sign-tool 0.2.6.1-1 1.0.16-1 } 
 {deepin-elf-verify 签名验证工具 deepin-elf-verify 0.1.0.5-1 1.0.16-1 }
 {org.deepin.contacts 联系人 deepin-contacts 2.0.11-1 2.1.12-1 } 
 {uos-browser-stable 浏览器 uos-browser 5.2.1500.0-1 5.2.1500.0-1 }
]
```





要更新的：

update_infos. json

```js
{
    "Package":"org.deepin.contacts",
    "CurrentVersion":"2.0.11-1",
    "LastVersion":"2.1.12-1",
    "ChangeLog":""
}
```



所有的应用：

```js
"org.deepin.contacts":{
    		"category":"chat","name":"联系人",
            "package_name":"org.deepin.contacts",
            "locale_name":{"en_US":"Contacts","zh_CN":"联系人"}}
```



呈现格式：

```json
		info := ApplicationUpdateInfo{
			Id:             id,
			Name:           aInfo.LocaleName[lang],
			Icon:           iInfos[id],
			CurrentVersion: uInfo.CurrentVersion,
			LastVersion:    uInfo.LastVersion,
		}

{org.deepin.contacts 联系人 deepin-contacts 2.0.11-1 2.1.12-1 } 
```



要更新的：

![image-20210727151749914](picture/image-20210727151749914.png)



所有的应用：

![image-20210727151800902](picture/image-20210727151800902.png)





