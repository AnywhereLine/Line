# Line


opkg update 更新软件库

opkg install luci

opkg install luci-i18n-base-zh-cn



opkg install shadowsocks-libev-config shadowsocks-libev-ss-local shadowsocks-libev-ss-redir shadowsocks-libev-ss-rules shadowsocks-libev-ss-tunnel luci-app-shadowsocks-libev




# Filebrowser


（1）apt install curl

（2）curl -fsSL https://filebrowser.xyz/get.sh | bash

当安装好之后，你并不能立即使用它，需要修改一些配置。修改配置如下：

（3）创建配置数据库：sudo filebrowser -d /etc/filemanager/filebrowser.db config init

（4）设置监听地址：sudo filebrowser -d /etc/filemanager/filebrowser.db config set --address 0.0.0.0 （这个地方可以改成自己服务器地址如10.10.2.250）

（5）设置监听端口：sudo filebrowser -d /etc/filemanager/filebrowser.db config set --port 8088 (端口配置的时候，首先查询一下端口是否被占用，使用一个没有被占用的端口)

（6）设置语言环境：sudo filebrowser -d /etc/filemanager/filebrowser.db config set --locale zh-cn （不设置的话直接默认英文，当然也可以先 
（7）设置日志位置：sudo filebrowser -d /etc/filemanager/filebrowser.db config set --log /var/log/filebrowser.log

（8）添加一个用户：sudo filebrowser -d /etc/filemanager/filebrowser.db users add root password --perm.admin，其中的root和password分别是用户名和密码，根据自己的需求更改。

(注意前面的每条命令前加上sudo，否者没有执行权限)

（9）启动file browser



配置修改好以后，就可以启动 File Browser 了，使用-d参数指定配置数据库路径。示例：filebrowser -d /etc/filemanager/filebrowser.db >/dev/null &

（10）开机启动file browser

cd /data/ES/
vim startes.sh
 
#!/bin/bash
filebrowser -d /etc/filemanager/filebrowser.db >/dev/null &
chmod +x startes.sh
sh startes.sh

vim /etc/rc.local
sh /data/ES/startes.sh
 
chmod +x /etc/rc.local
 
