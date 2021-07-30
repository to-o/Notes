### UOS更新种类的分类

`描述：`存在一个所需要更新的json文件，更新的json文件与包含所有应用的json文件进行匹配，匹配到一个包名就记录下来，包括记录图标



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





/usr/bin/lastore-tools update -j=update_infos -output=$UPDATE_INFO



获取要更新的所有软件包 `code：listDistUpgradePackages` 

```sh

sudo apt-get dist-upgrade --assume-no -o Debug::NoLocking=1
```





