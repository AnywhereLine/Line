# Line


opkg update 更新软件库

opkg install luci

opkg install luci-i18n-base-zh-cn



opkg install shadowsocks-libev-config shadowsocks-libev-ss-local shadowsocks-libev-ss-redir shadowsocks-libev-ss-rules shadowsocks-libev-ss-tunnel luci-app-shadowsocks-libev




# Filebrowser


apt install curl

curl -fsSL https://filebrowser.xyz/get.sh | bash

当安装好之后，你并不能立即使用它，需要修改一些配置

创建配置数据库：sudo filebrowser -d /etc/filemanager/filebrowser.db config init

设置监听地址：sudo filebrowser -d /etc/filemanager/filebrowser.db config set --address 0.0.0.0 

设置监听端口：sudo filebrowser -d /etc/filemanager/filebrowser.db config set --port 8088 

设置语言环境：sudo filebrowser -d /etc/filemanager/filebrowser.db config set --locale zh-cn 

设置日志位置：sudo filebrowser -d /etc/filemanager/filebrowser.db config set --log /var/log/filebrowser.log

添加用户：sudo filebrowser -d /etc/filemanager/filebrowser.db users add root root --perm.admin      
root用户名和密码

启动file browser

配置修改好以后 filebrowser -d /etc/filemanager/filebrowser.db >/dev/null &

开机启动file browser

新建一个脚本
vim startes.sh
写入内容

#!/bin/bash

filebrowser -d /etc/filemanager/filebrowser.db >/dev/null &

设置权限
chmod +x startes.sh

启动文件
sh startes.sh

写入系统启动项目开机自动启动
vim /etc/rc.local
sh /xxxx/xxxx/startes.sh
 
chmod +x /etc/rc.local
 
 # Nginx
 
 apt-get install nginx
 
 # mysql 
 
 apt-get install mysql-server mysql-client
