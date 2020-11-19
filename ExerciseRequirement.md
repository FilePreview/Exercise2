实验二任务要求

一、提交成果

​	《开源代码的泛读报告》,《代码质量分析报告》,报告模板和参考ftp上有，我也会上传。每个人写自己负责模块的泛读报告和分析报告，文件分别命名为"姓名-泛读报告","姓名-质量分析报告",上传到github上

二、泛读代码

​	1.方法级的注释应该为javadoc格式，如果已经有javadoc注释，使用块注释;语句的注释也使用块注释.注释的格式如下

```java
/*
 *  Author: Qin Huihuang   Date: 2020-11-17
 *  
 *  这个方法实现了....
 */
```

​     2.泛读完一个包之后，完成相应泛读报告中相应表格的撰写，示例如下：

![image-20201117105241018](C:\Users\Aaron\AppData\Roaming\Typora\typora-user-images\image-20201117105241018.png)

​	3.同时画出类间的关系图，示例如下；如果包中的类没有关系，可以略过；不需要包含类的属性和方法

![image-20201117105611433](C:\Users\Aaron\AppData\Roaming\Typora\typora-user-images\image-20201117105611433.png)

三、分析代码质量

1.  配置SonarQube代码质量分析工具(可视化，界面更加友好)，下载包我已经上传了。由于SonarQube8.5已经不支持Mysql数据库了，推荐大家使用Postgresql(使用其它也可以)。配置方式参考https://www.cnblogs.com/Simple-Small/p/12882948.html。配置完成之后，进入到bin/windows-x86-64，运行StartSonar.bat文件，等待启动成功之后，在浏览器输入localhost:9000即可进入snorqube(大家可以配置汉化插件，具体方式可以自行搜索)。snorqube的使用(点击开始分析项目，会有相应的提示)。分析完成之后的页面如下：

   ![image-20201117104028912](C:\Users\Aaron\AppData\Roaming\Typora\typora-user-images\image-20201117104028912.png)

   bugs级别的问题要求写入质量分析报告(每个人写自己负责包下面的bugs)，如果自己发现bug也可以写入质量分析报告.格式参考如下，代码截图后面应该是对问题的详细描述（这个详细描述在snorqube中有，大家可以借鉴）

   ![image-20201117105853268](C:\Users\Aaron\AppData\Roaming\Typora\typora-user-images\image-20201117105853268.png)

   异味级别的问题不需要写入质量分析报告。Note:发现的bugs和异味可以在实验二中就修改，修改之后确保程序仍然可运行。在修改的地方协商相应的块注释，注释格式如下：

   ```java
   /* 
    * Author: Qin Huihuang Modified: 2020-11-17
    * Question: 问题简要描述
    */
   ```

三、前端工作：

FilePreview项目使用的是MVC,2个人看这个项目中与MVC相关的代码，搞清楚控制流程，什么操作由什么Controller控制，调用的后台什么服务，产生什么View，数据传送需要什么(结果以图片方式展示，不需要对代码进行详细注释)

FielMananger项目主要使用的是Angular和SpringBoot MVC,2个人看这个项目，文件的移动，复制，下载，权限管理有关的内容全部不要，只需要展示文件结构和预览的功能。同样以图片的方式展示控制过程。

Note:FileManager项目编译完成之后，修改application.properties下的filemanager.root为电脑的一个目录地址，例如改为filemanager.root=C:\\Users\\Aaron\\Pictures之后运行项目，在浏览器输入localhost:8888即可