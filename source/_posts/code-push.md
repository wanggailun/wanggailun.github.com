---
title: code-push
categories:
  - 记录
tags:
  - ionic
  - cordova
  - code-push
date: 2021-09-22 17:40:00
---
ionic/cordova使用code-push更新js资产变更
<!--more-->
* code-push之前基于微软的appcenter服务器  
* 不过2022.4月appcenter将停止对cordova支持  
* 估采用code-push-server自建服务，[相关资料下载](/images/code-push-server.zip)  

注： code-push只是用于js等前端资产更新，不适用用涉及native变更的更新
1. 说明
   code-push-server，为code-push后端服务端程序，
2. 背景
   之前code-push使用的是微软的appcenter,但是appcenter2022.4月将不再支持cordova程序，估需要使用code-push-server，自己搭建code-push后端服务，让app连接自己搭建的服务
3. 环境
   nodejs@laster, mysql, redis
   npm install -g code-push-server
   npm install -g pm2
4. 配置
   初始化数据库
   code-push-server-db init --dbhost "localhost" --dbport "3306"  --dbuser "root" --dbpassword ""
   检查config.js配置
   重点是mysql, redis和downloadUrl配置
   *downloadUrl必须是外网可以访问的地址
5. 启动
   pm2 start process.json
```
   弃用
   1. 使用的是微软的code-push，需要用到微软的appcenter服务器(用于存放要更新的资源)  
   2. 打开 https://appcenter.ms/，注册登录  
   3. 点击add new app创建app(最好各平台一个app，例如myapp-android，myapp-ios)  
   4. 点击某个app,点击Distrivute,选择CodePush  
   5. 右上角扳手图标出来环境管理面板，名字可以自己改 dev dev2 release等  
   6. 重点是复制环境对应的key,后边根据key检查更新
```
6. ionic项目安装code-push插件
   1. ionic cordova plugin add cordova-plugin-code-push
   2. npm install --save @ionic-native/code-push@4(ionic3/4封装的可能需要带@4,具体看文档)
7. 使用插件
   1. 是哟个sync方法 执行默认是检查下载app下次重启后生效，
      * option可配置安装模式，是否弹窗，sync还可监听下载进度等
      * 文档地址： 
        https://docs.microsoft.com/zh-cn/appcenter/distribution/codepush/cordova    
        ```
        public checkUpdate(){  
           let option = {deploymentKey:'qIKeakxYbNMZz_qZGBgJU-knPGh6mBiHers8q'};    
           this.codePush.sync(option);  
        }
        ```
8. 发布更新  
   1. 安装code-push
      npm install -g code-push@2.1.9
   2. 登录
      命令行执行: code-push login 服务器地址(http://localhost:3000)
      会自动打开浏览器登录完有个token，复制填入命令行继续
   3. 查看app列表
      code-push apps list
      code-push app add test android cordova
      code-push deployment list test -k
      code-push deployment add dev
   4. 在项目根目录执行发布
      先ionic cordova build android/ios --prod   
      build后平台下边就会有各自的资源文件
      code-push release test ./platforms/android/app/src/main/assets/www 1.0.0 -d dev
10. 测试
    1. 先安装插件，方个按钮，调用上边那个checkUpdate方法，key记得改下
    2. 运行到手机上
    3. 界面内容改下，build下，执行发布
    4. 手机上点下更新按钮观察日志，日志会输出检查详情
    5. 重启app,看下效果
