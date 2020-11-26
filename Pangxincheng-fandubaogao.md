# kkFileView开源代码的泛读报告

<p align="right">2018303012 庞新程</p>

## 1.    列出kkFileView中的类及各类的主要作用

表1 kkFileView的代码构成及主要作用

| 包            | 子包 | 类                                | 主要作用                                              |
| ------------- | ---- | --------------------------------- | ----------------------------------------------------- |
| jodcconverter | cli  | Convert                           | 命令行启动文件格式转换器                              |
| document      |      | DefaultDocumentFormatRegistry     | 默认的文档注册表(配置了对各种文件的支持)              |
| document      |      | DocumentFamily                    | 一个枚举类,包含了一些格式族                           |
| document      |      | DocumentFormat                    | 文档格式的具体类,定义了一个文件的格式信息             |
| document      |      | DocumentFormatRegistry            | 文档格式注册表接口                                    |
| document      |      | JsonDocumentFormatRegisty         | 解析JSON字符串中的配置的文档格式                      |
| document      |      | SimpleDocumentFormatRegisty       | 简单的文档注册表,实现了DocumentFormatRegistry中的方法 |
| office        |      | DefaultOfficeManagerConfiguration | OfficeManager的配置文件                               |
| office        |      | ExternalOfficeManager             | 连接外部office的管理器,用于管理task                   |
| office        |      | OfficeManager                     | 管理office task的接口                                 |

## 2. 类间关系图

根据kkFileView的开源代码，绘制其体系结构图。(类间继承管理由Idea导出)

文档格式注册表的类间的继承关系

<img src="https://gitee.com/pangxincheng/Images/raw/master/1606187848842.png"/>

<img src="https://gitee.com/pangxincheng/Images/raw/master/1606187883286.jpg"/>

调用关系图

<img src="https://gitee.com/pangxincheng/Images/raw/master/1606187779149.jpg"/>

## 3. 列车kkFileView的基本功能

根据对kkFileView代码的阅读和功能的理解，描述了kkFileView的整体功能框架和主要功能。

​		kkFileView分为两个模块: jodcconverter-core和jodcconverter-web

​		jodcconverter-web是本软件的web模块，负责与前端进行交互

​		jodcconverter-core模块是负责文件转换的核心模块，其他的模块可以调用其main函数来启动文件格式转换，其主要功能便是文件格式转换。

​		jodcconverter-core提供了用命令行启动的方式(从其他的模块调用此方法也可以启动转换，原理是一致的)，下面将从命令行启动方式来阐述其整体功能框架。

​		jodcconverter-core的命令行启动类是org.artofsolving.jodconverter.cli.Convert。这个类使用了apache的命令行解析包org.apache.commons.cli.*。在启动时，需要从命令行传参，支持传入的参数如下：

- 指定文件输出格式：-o xxx 或者 --output-format xxx

- Office的socket端口号：-p xxxx 或者 —port xxxx

- 文档格式注册表配置文件(可选,json格式)：-r xxx 或者 –registry xxx

- 最大转换的等待时间(可选，默认是120s)：-t xxx 或者 –timeout xxx

- 使用给定用户安装目录中的设置(可选)：-u xxx 或者 –user-profile xxx

- 源文件名

- 目标文件名

 

​		其主函数的工作原理如下：

​		首先创建一个命令行解析器(CommandLineParser)，然后使用这个解析器去解析传入的参数，将解析结果保存在CommandLine的一个对象中，接下来调用CommandLine中的方法尝试拿到相关的参数，如果缺少相关参数并且该参数是可选的，就使用默认参数，否则输出提示信息，然后退出系统。

​		下一步创建一个OfficeManager，尝试连接到office，成功后会创建一个转换器，然后便通过转换器的convert函数从源文件转换为目标文件(如果没有指定文档格式的话，convert会尝试直接转换，否则会转换为配置的格式，而不管目标文件名中是否带了拓展名)

​		转换完成后，断开到office的连接，转换工作完成。

## 4. 软件功能与类间的对应关系

| 序号 | 功能名称             | 实现模块                               | 实现方法                     |
| ---- | -------------------- | -------------------------------------- | ---------------------------- |
| 1    | 文件格式转换的启动类 | org.artofsolving.jodconverter.cli      | main                         |
| 2    | 文件格式转换的配置类 | org.artofsolving.jodconverter.document | DocumentFormatRegistry(接口) |
| 3    | office的管理器       | org.artofsolving.jodconverter.office   | OfficeManager(接口)          |
| 4    | 进程管理器           | org.artofsolving.jodconverter.process  | ProcessManager(接口)         |
| 5    | 辅助工具             | org.artofsolving.jodconverter.util     | PlatformUtils                |

## 5. 收获

​		在阅读源码的时候，发现了原来的一个bug，对于win10家庭版的用户，使用命令行启动时会报错，相关的dll文件也已经导入到系统文件夹下，在DefaultOfficeManagerConfiguration默认的office的配置类中，它会尝试findBestProcessManager，然而可能是权限的问题，它要使用org.hyperic.sigar.Sigar包下的进程管理器，无论怎么使用都是报错，我们暂时将它去掉了，然后使用的是PureJavaProcessManager这个进程管理器(Linux下会使用LinuxProcessManager)，便可以正常工作。下一步可以看一下SigarProcessManager，修改掉这个bug。

## 6. 存在的问题

暂无