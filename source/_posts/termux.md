---
title: termux基础
date: 2021-11-1 15:40:00
categories: 
- 记录
tags:
- termux
- mysql
- php
- nginx
- ssh
---
废旧手机再利用，使用termux搭建服务器
<!--more-->
手机安装termux.apk  

apt update  更新软件库  
apt upgrade  

apt install termux-services    //安装termux-services(服务管理)  
apt install openssh            //安装ssh(远程终端连接)  
ps aux|grep sshd               //查看是否正在运行  
lsof -i:8022				   //检查端口占用  
sv-enable sshd                 //使用sv设置自启  

1000一下端口需要root(android低端口安全)  

电脑和手机在统一局域网  
windows使用xshell  
https://www.netsarang.com/zh/free-for-home-school/  
https://blog.csdn.net/qq_35891887/article/details/114972783  
或者使用cmd连接   ssh 手机ip -p 8022  

根目录  $PREFIX(files/usr) 或 /data/data/com.termux/files/ 或 $home/../  
passwd       修改用户密码(termux用户名是android系统分配的，不能修改)  


apt install android-tools  
开启adb无线(可以编辑~/.baserc文件,将下边的加入到自启)  
sudo setprop service.adb.tcp.port 5555 &  
sudo stop adbd &  
sudo start adbd &  

apt install nodejs  
apt install vim  

apt install tsu  //安装tsu(代替su sudo)  
tsu .../ su .../ sudo ..  //使用  

apt install termux-api  
termux-setup-storage   //会在当前目录生成storage目录，指向sd卡  
termux-wake-lock	   //锁屏保持  
ln –s filename link_filename  连接文件(创建快捷方式)  
rm -rf  ./test_chk_ln		正确的删除方式（删除软链接，但不删除实际数据）  
rm -rf ./test_chk_ln/ (这样就会把原来test_chk下的内容删除)错误的删除方式  

apt install redis  //安装redis  
ln -s ~/redis.conf		//连接config文件到当前目录  
vim ~/redis.conf 		//把daemonize设置为yes  
echo "redis-server ~/redis.conf" >> ~/.bashrc	//设置自启  
ps aux|grep redis  

apt install nginx  
sv-enable nginx  
cd $home & mkdir nginx  
ln –s nginx/config $prefix/usr/etc/nginx  
ln –s nginx/html $prefix/usr/share/nginx/html  
ln –s nginx/config $prefix/usr/var/log/nginx  

apt install php-fpm  
vim $PREFIX/etc/php-fpm.d/www.conf  
注释掉user group  
listen = /data/data/com.termux/files/usr/var/run/php-fpm.sock 直接修改为：listen = 127.0.0.1:9000  
vim $PREFIX/etc/nginx/nginx.conf  
index index.html index.htm;改为index index.html index.htm index.php;  
增加  
```
location ~\.php$ {
root           html;
fastcgi_pass   127.0.0.1:9000;
fastcgi_index  index.php;
fastcgi_param  SCRIPT_FILENAME  /data/data/com.termux/files/usr/share/nginx/html$fastcgi_script_name;
include        fastcgi_params;
}
```
启动  
sv-enable php-fpm  

apt install mariadb		//安装mysql  
mysql_install_db		//初始化数据库  
sv-enable mysqld		//启动设置自启  
ps aux|grep mysql		//查看运行  
sv down mysqld			//停止  
mysql -u $(whoami)		//使用当前用户登录  
use mysql;				//登陆后切换数据库  
set password for 'root'@'localhost' = password('YOUR_ROOT_PASSWORD_HERE');	//修改root密码  
grant all privileges on *.* to 'root'@'%' identified by '' with grant option;	//开启root远程登录  
flush privileges;	    //刷新  
quit;					//退出mysql登录  

// apt remove mariadb   //卸载  
// rm -r $PREFIX/var/lib/mysql/*  //清理数据库  

termux-services(服务管理支持的服务)sv-enable / sv up / sv down/ sv-disable (service)  
apache2			httpd	8080    
bitcoin			bitcoind	    
busybox			telnetd	8023    
busybox			ftpd	8021    
cronie			crond		    
emacs			emacsd		    
ipfs			ipfs		    
libmosquitto	mosquitto	1883	    
lighttpd		lighttpd	8080	    
lnd	lnd			Lightning     
mariadb			mysqld	3306	    
mpd				mpd			    
mpdscribble		mpdscribble		    
nginx			nginx	8080	    
openssh			sshd	8022	    
postgresql		postgres	5432	    
privoxy			privoxy		    
tor				tor			    
transmission	transmission  

