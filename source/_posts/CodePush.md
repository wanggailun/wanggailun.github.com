---
title: adb 无线连接教程
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
注： code-push只是用于js等前端资产更新，不适用用涉及native变更的更新
1. 使用的是微软的code-push，需要用到微软的appcenter服务器(用于存放要更新的资源)
   1. 打开 https://appcenter.ms/，注册登录
   2. 点击add new app创建app(最好各平台一个app，例如myapp-android，myapp-ios)
   3. 点击某个app,点击Distrivute,选择CodePush
   4. 右上角扳手图标出来环境管理面板，名字可以自己改 dev dev2 release等
   5. 重点是复制环境对应的key,后边根据key检查更新
2. ionic项目安装code-push插件
   1. ionic cordova plugin add cordova-plugin-code-push
   2. npm install --save @ionic-native/code-push@4(ionic3/4封装的可能需要带@4,具体看文档)
3. 使用插件
   1. 是哟个sync方法 执行默认是检查下载app下次重启后生效，
      * option可配置安装模式，是否弹窗，sync还可监听下载进度等
      * 文档地址： https://docs.microsoft.com/zh-cn/appcenter/distribution/codepush/cordova  
         public checkUpdate(){  
            let option = {deploymentKey:'qIKeakxYbNMZz_qZGBgJU-knPGh6mBiHers8q'};    
            this.codePush.sync(option);  
         }
4. 发布更新  
   1. 安装appcenter
      npm install -g appcenter-cli
   2. 登录
      命令行执行: appcenter login
      会自动打开浏览器登录完有个token，复制填入命令行继续
   3. 查看app列表
      appcenetr apps list
   4. 在项目根目录执行发布
      先ionic cordova build android/ios --prod   
      build后平台下边就会有各自的资源文件  
      appcenter codepush -d 环境名(比如dev什么的) -a app名(上边列出来的完整app名) -c 资源目录路径(android是指向assets/www目录相对路经，ios也是) -t 版本号(那个版本可以更新这可发布)
5. 测试
   1. 先安装插件，方个按钮，调用上边那个checkUpdate方法，key记得改下
   2. 运行到手机上
   3. 界面内容改下，build下，执行4.4发布
   4. 手机上点下更新按钮观察日志，日志会输出检查详情
   5. 重启app,看下效果
