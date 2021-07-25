###  开源代码

- `注:`此文档为一些总结和开源文档的翻译具体实现细节参考官方文档
- 文档：https://docs.activitywatch.net/en/latest/getting-started.html
- code：https://github.com/ActivityWatch/activitywatch



### 开源的权限

- 使用MPL 2.0协议同著名的GPL许可证和BSD许可证相比，MPL在许多权利与义务的约定方面与它们相同

- 商业软件可以使用修改后的代码版权归软件的发起者。

  



### 流程图

![image-20210722173045634](picture/image-20210722173045634.png)



### 目录

目录结构的控制代码在`aw-core/dirs.py` 

- 详细资料参考：https://docs.activitywatch.net/en/latest/directories.html

- ```sh
  - 配置文件目录 `~/.config/activitywatch` 
  - log日志目录 `~/.cache/activitywatch/log`
  - 缓存位置 `~/.cache/activitywatch`
  - 数据 `~/.local/share/activitywatch`
  
  ```

  

### 数据模型

源文档链接：https://docs.activitywatch.net/en/latest/buckets-and-events.html

数据模型为此监控功能的核心，数据的传输和存储定义

#### Buckets 

- 简介：每个Buckets 都包含一系列的事件和这些事件的元数据（如它们的类型和收集它们的东西），每一个观察器都有一个Bucket，一个Bucket应该总是从同一个来源接收数据。例如如果想写一个观察器来追踪当前活跃的窗口，我们首先创建一个Bucket然后开始报告事件到这个Bucket中（使用心跳完成）

- 数据格式

  ```json
  bucket = {
    "id": "aw-watcher-test_myhostname",
    "created": "2017-05-16T13:37:00.000000",
    "name": "A short but descriptive human readable bucketname",
    "type": "com.example.test",       // Type of events in bucket
    "client": "example-watcher-test", // Identifier of client software used to report data
    "hostname": "myhostname",         // Hostname of device where data was collected
  }
  ```

  

#### Events

所有的时间戳被存储使用的是UTC时间，会存在时区的偏差，目前这些时间差的处理在显示数据客户端进行处理计算偏差。所查询出来的时间都是会存在偏差的

- json格式

  ```js
  event = {
    "timestamp": "2016-04-27T15:23:55Z",  // ISO8601 formatted timestamp
    "duration": 3.14,                     // Duration in seconds
    "data": {"key": "value"},  // A JSON object, the schema of this depends on the event type
  }
  ```

  

#### Heartbeats

Heartbeats是为了合并具有相同数据的相邻事件（`pulsetime`在一个时间窗内），这样做有利于保存数据在硬盘上。

合并事件A和B如果他们`data`是相同的和时间戳是在`pulsetime`在一个时间窗内。由此产生的事件将具有更早的时间戳，一个持续时间，以配合时间戳之间的差异。

查看例子 [`aw_transform.heartbeat_merge()`](https://docs.activitywatch.net/en/latest/api/python.html#aw_transform.heartbeat_merge) or the [heartbeat REST API](https://docs.activitywatch.net/en/latest/api/rest.html#heartbeat-api).

此`heartbeat REST API`为经常使用的API客户端请求数据到服务端

```http
POST /api/0/buckets/<bucket_id>/heartbeat
```



#### Event types

##### currentwindow 窗口

- 数据格式

  ```json
  {
      app: string,
      title: string,
  }
  ```

##### afkstatus AFK 鼠标键盘

- 数据类型

  ```json
  {
      status: string   // "afk" or "not-afk"
  }
  ```



其他事件类型待完善



### API 参考

#### REST API

在ActivityWatch中客户端与服务端的通信都使用的是REST API，









### 代码结构

`aw-core` ActivityWatch 的核心库 其他的库都会调用这个库的组件 

- `aw_core`  包含了基础的数据类型和工具，比如`Event`类、用于配置的辅助工具、日志和buckets、事件、导出等等
- `aw_datastore`  包含了数据存储类被aw-server-python使用
-  `aw_transform` 查询中使用的所有事件转换。
- `aw_query` ActivityWatch 使用的查询语言



`aw-client ` ActivityWatch 的客户端库各种API主要作为两种

- 一个观察器调用API发送数据到服务器端来存储
- 一个显示获取数据 
- 其中数据的存储和发送都是到`aw-server`
- 客户端和服务端进行交互使用的是 `REST API`(get post)进行通信的



`qw-qt` 目的：服务的管理 托盘图标



#### 服务器

`aw-server`  目的存储和检索收集的数据

- `aw-webui`搭建web界面使用`vus.js`来开发的界面

- `aw_server` 使用Flask来搭建web服务器

  

#### 观察器

`aw_watcher_afk` 目的检测鼠标键盘是否是活跃决定是否是AFK（away from keyboard 简称长时间没有移动鼠标或者敲击键盘）

- 记录鼠标和键盘的两个参数 一记录上一次`鼠标键盘移动的时间`和`两次鼠标移动的时间间隔`
- 通过超时来判断是否是AFK
- 使用心跳包来发送事件的间隔
- 配置中来设置超时和心跳间隔时间
- 提交一次事件

`aw_watcher_window` 观察活跃的窗口和它的标题

- 主要通过xlib获取窗口的名称和标题 再通过发送时间到收集数据的地方
- 间隔检测时间1S 记录时间发送心跳包到服务端

`总结`：其中收集数据的观察器不难 主要是所有数据的分析 展示一些数据





提示：

所有的模块开启debug模式使用 例如`aw-watcher-window --testing`





### 观察器详细介绍

#### aw_watcher_afk模块

`目的`：检测鼠标键盘是否是活跃决定是否是AFK（away from keyboard 简称长时间没有移动鼠标或者敲击键盘）

`建立流程:`

1. 导入配置包括轮询时间设置
2. 设置log配置记录
3. 调用ActivityWatchClient实现一个客户端的建立（`ActivityWatchClient` 一个围绕aw-server REST API的方便的封装器。是与服务器交互的推荐方式。）
4. 创建一个create_bucket，注意一个观察器建立一个bucket，类似于用于存放所有数据的一个bucket
5. 心跳循环发送当前活跃窗口的应用和标题名字（通过`Xlib`）

<img src="picture/image-20210724165802157.png" alt="image-20210724165802157" style="zoom:80%;" />







`注意点:`

- 其中主要的GET，POST采用异步的任务队列来出来每一个任务

  ```
  请求：http://localhost:5600/api/0/buckets/ 等等
  
  ```

  



### 总结

- 服务器与客户端通信http的REST，客户端类定义了与客户端通信aw-server REST API，以推荐的方式与服务器进行交互
- 数据库使用的为peewee来实现的
- 





### 存在的问题

- 当点击计算器时窗口被计算器捕获，但是当不使用计算器 鼠标移动到其他地方但是焦点还在计算器上就会造成计算器时间一直增加





### 观察器种类

特性：支持开发插件做自己的观察器

窗口程序

- [aw-watcher-afk](https://github.com/ActivityWatch/aw-watcher-afk)  观察鼠标和键盘的活动来检测是否用户是活跃的
- [aw-watcher-window](https://github.com/ActivityWatch/aw-watcher-window) 观察活跃的窗口和它的标题

浏览器

- [aw-watcher-web ](https://github.com/ActivityWatch/aw-watcher-web) 观察浏览器活跃的页的标题、URL、隐秘状态

编辑器

介绍：观察活跃的编辑文件和相关的元数据如路径、语言、项目名称等等

- [aw-watcher-vim](https://github.com/ActivityWatch/aw-watcher-vim) - vim extension, by [@johan-bjareholt](https://github.com/johan-bjareholt) and [@ahnlabb](https://github.com/ahnlabb).
- [aw-watcher-vscode](https://github.com/ActivityWatch/aw-watcher-vscode) - Visual Studio Code extension, by [@Otto-AA](https://github.com/Otto-AA).
- [pauldub/activity-watch-mode](https://github.com/pauldub/activity-watch-mode) - emacs mode forked from wakatime-mode, by [@pauldub](https://github.com/pauldub).
- [OlivierMary/aw-watcher-jetbrains](https://github.com/OlivierMary/aw-watcher-jetbrains) - JetBrains IntelliJ plugin, by [@OlivierMary](https://github.com/OlivierMary).
- [LaggAt/ActivityWatchVS](https://github.com/LaggAt/ActivityWatchVS) - Visual Studio extension, by [@LaggAt](https://github.com/LaggAt)
- [pascalwhoop/aw-idea](https://github.com/pascalwhoop/aw-idea) - (WIP) JetBrains IntelliJ IDEA/PyCharm/WebStorm/etc extension forked from wakatime, by [@pascalwhoop](https://github.com/pascalwhoop)
- [kostasdizas/aw-watcher-sublime](https://github.com/kostasdizas/aw-watcher-sublime) - Sublime Text 3, by [@kostasdizas](https://github.com/kostasdizas) (unmaintained)
- [prplecake/aw-watcher-sublimetext](https://github.com/prplecake/aw-watcher-sublimetext) - Sublime Text 3, by [@prplecake](https://github.com/prplecake) (fork of aw-watcher-sublime above, maintained)
- [NicoWeio/aw-watcher-atom](https://github.com/NicoWeio/aw-watcher-atom) - Atom, by [@NicoWeio](https://github.com/NicoWeio)



媒体观察器



其他的观察器

- [Alwinator/aw-watcher-table](https://github.com/Alwinator/aw-watcher-table) 监视你是否将高度可调的状态栏设置为横或竖
- [aw-watcher-input](https://github.com/ActivityWatch/aw-watcher-input)  监控按键的数量和鼠标移动的距离
- [aw-watcher-tmux](https://github.com/akohlbecker/aw-watcher-tmux) 监控终端的
- 

