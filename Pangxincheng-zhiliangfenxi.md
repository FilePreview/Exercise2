问题严重程度: CRITICAL

简要描述:

命令行启动转换工具启动失败

截图

<img src="https://gitee.com/pangxincheng/Images/raw/master/1606187928137.jpg"/>

详细描述:

对于win10家庭版的用户，使用命令行启动时会报错，相关的dll文件也已经导入到系统文件夹下，在DefaultOfficeManagerConfiguration默认的office的配置类中，它会尝试findBestProcessManager，然而可能是权限的问题，它要使用org.hyperic.sigar.Sigar包下的进程管理器，无论怎么使用都是报错