 ##  providers/

### translation.js: 

> 国际化
>
> - en 英语
> - he 希伯来语
> - pt 葡萄牙语
> - es 西班牙语
> - fr 法语
> - de 德语
> - sk 斯洛伐克语
> - zh 汉语
> - ru 俄语
> - ua 乌克兰语
> - tr 土耳其语
> - fa 波斯语
> - pl 波兰语

### config.js: 

> 配置文件，匿名自调用函数
>
> - values :  配置信息描述值
> - 通过url配置文件路径 
> - 一些其他配置如 默认使用面包屑、使用ajax下载文件，默认不适用异步压缩解压缩

## filters/

### filters.js: 


> 通过key值映射，选择不同功能的过滤
>
> - 'formatDate' : 格式化日期
> - 'humanReadableFileSize': 可视化文件
> - 'fileExtension': 过滤构造选择
> - 'strLimit': 过滤太长字符串

## services/

### apihandler.js:  

> 前端接口方法文件
>
> - deferredHandler: 过滤非法data \ code 请求，初始化响应deffered，处理响应
> - list: 展示文件列表
> - copy: 复制文件
> - move: 移动文件
> - remove：移除文件
> - upload: 上传文件
> - getContent: 获取文件内容
> - edit: 编辑文件
> - rename: 重命名文件
> - getUrl: 获取地址url地址
> - download: 下载
> - downloadMultiple: 多文件下载
> - compress：压缩
> - extract：解压
> - changePermissions：修改权限
> - createFolder：创建文件夹

### apimiddleware.js:  

>  前端接口中间件 封装模块并导出  调用apihandler
>
> - getPath：获取目标地址
> - getFileList：获取文件列表
> - getFilePath：获取文件地址
> - list: 展示文件列表
> - copy: 复制文件
> - move: 移动文件
> - remove：移除文件
> - upload: 上传文件
> - getContent: 获取文件内容
> - edit: 编辑文件
> - rename: 重命名文件
> - getUrl: 获取地址url地址
> - download: 下载
> - downloadMultiple: 多文件下载
> - compress：压缩
> - extract：解压
> - changePermissions：修改权限
> - createFolder：创建文件夹

### filenavigator.js:  

> 注册业务模块
>
> - deferredHandler：过滤非法data \ code 请求，初始化响应deffered，处理响应
> - list：获取文件列表
> - refresh：刷新页面
> - buildTree：重构目录树
> - folderClick：点击文件夹响应
> - upDir：返回上一级
> - goTo：页面跳转
> - FileNameExists：判断文件名是否存在
> - ListHasFolders：判断文件列表中是否有文件夹



