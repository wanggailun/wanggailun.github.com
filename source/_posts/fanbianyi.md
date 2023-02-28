---
title: APK反编译
date: 2023-02-28 14:47:00
categories: 
- 记录
tags:
- apk
- 反编译
- android
---
APK反编译修改后重新打包
<!--more-->
=====[点击下载工具包](/images/fanbianyi.zip)
1. 本地需要android开发环境
2. 反解APK到test目录(可直接修改smali目录中的smali代码):  
`SET BAT_HOME=%~dp0/tools/apktools && apktool d test.apk`  
3. 改为zip解压获取dex，并将dex转为jar(阅读逻辑)  
`SET BAT_HOME=%~dp0/tools/dex2jar && d2j-dex2jar.bat classes.dex`  
`SET BAT_HOME=%~dp0/tools/dex2jar && d2j-dex2jar.bat classes2.dex`  
4. 使用jd-gui.exe阅读jar  
`start tools/jd-gui.exe ../classes-dex2jar.jar`
5. 改为debug包  
`AndroidManifest.xml中的application节点添加android:debuggable="true"`
7. 打包到test1.apk  
`SET BAT_HOME=%~dp0/tools/apktools && apktool b test -o test1.apk`  
8. 签名密码123456  
`jarsigner -verbose -keystore ./tools/test.keystore -signedjar test-sign.apk test1.apk test`  

