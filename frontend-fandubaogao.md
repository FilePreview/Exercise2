## Augular一步一步渲染出最终页面

1. 浏览器的事件回路一直等待着事件的触发，事件包括用户的交互操作、定时事件或者网络事件（如服务器的响应等）；

2. 一旦有事件触发，就会进入到Javascript的context中，一般通过回调函数来修改DOM

3. 等到回调函数执行完毕之后，浏览器又根据新的DOM来渲染新的页面

   

![](C:\Users\26731\Desktop\事件.jpg)



## 当用浏览器访问index.html的时候，浏览器依次执行

1. 加载html，然后解析成DOM；

2. 加载angular.js脚本；

3. AngularJS等待DOMContentLoaded事件的触发；

4. AngularJS寻找ng-app指令，根据这个指令确定应用程序的边界；

5. 使用ng-app中指定的模块配置$injector；

6. 使用$injector创建$compile服务和$rootScope；

7. 使用$compile服务编译DOM并把它链接到$rootScope上；

8. ng-init指令对scope里面的变量name进行赋值；

9. 对表达式{{name}}进行替换，于是乎，显示为“Hello World!”     

   

![](C:\Users\26731\Desktop\访问.png)



### index.html

```HTML
<!doctype html>
<html ng-app>
  <head>
    <script src="angular.js"></script>
  </head>
  <body>
    <png-init=" name='World' ">Hello {{name}}!</p>
  </body> 
</html>
```

| 文件                           | 主要作用                                     |
| ------------------------------ | -------------------------------------------- |
| animations.css                 | 动画样式                                     |
| dialogs.css                    | 对话框样式                                   |
| main.css                       | 所有样式表                                   |
| main.js                        | 主要功能注册入口                             |
| selector-controller.js         | 注册选择器控制器模块                         |
| directives.js                  | 注册文件管理器                               |
| chmod.js                       | 注册chomd类模块                              |
| item.js                        | 注册item类模块                               |
| filters.js                     | 过滤器模块                                   |
| config.js                      | 配置文件                                     |
| translations.js                | 国际化                                       |
| apihandler.js                  | 前端接口方法文件                             |
| apimiddleware.js               | 前端接口中间件 封装模块并导出 调用apihandler |
| filenavigator.js               | 文件导航框模块                               |
| app.js                         | 应用程序入口                                 |
| current-folder-breadcrumb.html | 当前文件夹面包屑导航                         |
| item-context-menu.html         | 右键菜单                                     |
| main.html                      | 页面                                         |
| main-icons.html                | 页面图标                                     |
| main-table.html                | 页面表格                                     |
| main-table-modal.html          | 页面表格模型                                 |
| modals.html                    | 模型列表                                     |
| navbar.html                    | 导航条                                       |
| sidebar.html                   | 侧边栏                                       |
| spinner.html                   | 动画                                         |