# __launchpad环境搭建、PGP密钥上传和PPA包上传__
## __1. 环境搭建__
```
(1)	在/etc/hosts文件中增加字段   
172.20.191.4    launchpad.dev    
172.20.191.4    archive.launchpad.dev    
172.20.191.4    ppa.launchpad.dev    
(2)	在/etc/resolv.conf文件中增加字段    
    nameserver	172.20.191.2    
(3)	将DNS网段改为172.17.50.100
```
## __2.	登录launchpad.dev__     
```
(1)	账户：姓名
(2) 密码：
```
## 	__3. 秘钥配置__
```
(1)	创建密钥	
	#gpg --gen-key
(2)	查看生成的密钥	
	#gpg --list-key
    pub   2048R/BA155DF1 2021-02-21
    uid                  hanteng <hanteng@kylinos.cn>
    sub   2048R/EDB8567C 2021-02-21
(3)	查看密钥指纹 
	#gpg --fingerprint BA155DF1
	pub   2048R/BA155DF1 2021-02-21
	密钥指纹 = 84F1 9EDA 5B37 9418 645B  C533 C66E 9AA0 BA15 5DF1
	uid                  hanteng <hanteng@kylinos.cn>
	sub   2048R/EDB8567C 2021-02-21
(4)	将密钥上传到launchpad.dev
	#gpg --keyserver launchpad.dev --send-keys BA155DF1
	(也可以直接上传密钥指纹)
	gpg: 将密钥‘BA155DF1’上传到 hkp 服务器 launchpad.dev
(5)	在launchpad.dev上导入密钥指纹
	Import an OpenPGP key
	Fingerprint：密钥指纹
	Import Key
(6)	登录邮箱去邮箱查看邮件
(7)	将邮件中的重要信息复制到文本文件中
    #cat 文本文件
    显示如下:
	-----BEGIN PGP MESSAGE-----
    hQEMA2P/zl/tuFZ8AQgAg8nwvrSB75yMbkv+M36GzWpR+oxXTaCr8qGBnfafx/os
    51QVXrPRw7yLUujxoTS0sKXATkt5PA6OATr2DIpbkyJIKzQc/YpLFxb/kCJNuUXd
    IP3y+VcrF5FJizcjtwrx69sQcR+q6hQrQ3K0ADIDowJq280k/w729SKnTbzMrVXq
    iFPuav14w+sGHFg8ZtxU47ayQ/Chbv023yr2Ck+u1xwu24veEh3FU48KrDB5ReiM
    9SZWLHNup9jsnz3kBSRMuqADvcNx9xkoMxyTDugfukjsRaTgZSBT6A6SzLTHo3Lb
    mLFepww2xNqBQWVPk7rOq4zPDJJxWoQkV9K1phFkmtLAqwHcNOkJZj+/MnwV7wbr
    RaXXk7joBnPtmMxVhCgSd4dN8JwjzIlNo2ee0/b2H46GMPmx5diArWCjpK9K5atn
    EAvhogz0lHkT6KWtyEUoAg6r4Z4iELu7gbzCHoTw1PvujPj+hOI+RJKUPJXoiP/M
    FvWJhxnwikcH/FjkGPPoiZyxqm7odcNgfIOylF81Y3C+/WMGTnqPimFBKhTjqRPJ
    6oCrQOgW4Bu869F2zNGJJcgZGtCCVN9qrZHtwi+IzO3F5HjQLwjUURnzNZ78FUlz
    VT9iWsdbRWI7Lm8oV0UGpcY4SrnuZSprGHc9a/dYm231suSRTf3/iCAVYA1Pn8Z2
    yDGiKlrfbrhprkmM/QW1OznEs5kHNImiCjf/ZKFwdE28CLFeGSXQnHXFmZVrpBxT
    s+YPMn9bwEC8+gtKSv7YMdQ+CRIJ1AXxof5qfo+okaegx72IDXcsMHdy7qoUCbx1
    LVQuMRaDcY1/Pe923Q==
    =8aiD
    -----END PGP MESSAGE-----
(8)	在终端中执行命令,会提示输入密码
    #gpg -d 文本文件
(9)	终端最下面有一行关于网址的链接
    Please go here to finish adding the key to your Launchpad account:
        https://launchpad.dev/token/xxxxxxxxxxxxxxxxxxxxxxx
    点击进入链接进行确认即可完成pgp导入
```
##  __4. PPA包上传__
```
(1) 建立PPA仓库
(2) debuild -S -sa 编包生成source.changes文件
(3) 使用dput指令上传source.changes文件
(4) 上传之后会在邮箱中收到一封邮件，如果有问题则会在邮件中指出错误的地方。如果没有则会邮件提示上传成功。
```
# __注意事项__
```
(1) #dput xxxxxxx指令上传的时候会提示：
	    No host devppa found in config
    在launchpad ppa上传的网页中有提示上传阅读手册，阅读手册更改.dput.cf文件即可正常上传文件
```
 hanteng  2020/02/23



```
[devppa]
fqdn = ppa.launchpad.dev:2121
method = ftp
incoming = ~%(devppa)s
login = anonymous

[dev]
fqdn = ppa.launchpad.dev:2121
method = ftp
incoming = /%(dev)s
login = anonymous
```

