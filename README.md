# filebrowser
Filebrowser 是一个非常好用的文件浏览器，本一键脚本在官方脚本基础上，增加自动化安装、更新主程序，配置好语言端口及密码，并设置systemctl自动启动等等功能，欢迎使用。

# 说明 
使用官方脚本下载，但官方脚本只有判断系统版本并自动下载主程序，缺乏功能，目前脚本会自动调用官方脚本下载主程序，然后写好可自启动的 filebrowser.service ，往后使用 systemctl start filebrowser 管理；        
本脚本会将主程序及数据库文件统一放置到 /opt/filebrowser/ 目录，而不是官方默认的 /usr/local/bin/ 避免在系统目录生成 /usr/local/bin/filebrowser.db 或使用 /etc/filebrowserfilebrowser.db 来存放；   

# 下载脚本并修改权限
```
wget https://raw.githubusercontent.com/petcat/filebrowser/refs/heads/main/filebrowser.sh && chmod +x filebrowser.sh
./filebrowser.sh
```

脚本会自动配置以下项目：监听本机 0.0.0.0 和 8090 端口，并设置程序语言为中文，并将日志写到 /var/log/filebrowser.log；   
脚本会询问你设置管理员用户名和密码，如直接回车，则使用默认 admin 用户名和随机生成16位密码。

# 升级及其他功能

`./filebrowser.sh -upgrade` 当有新版本可升级时，可升级更新，脚本会自动判断版本是否有更新，有则升级。   
`./filebrowser.sh -pw` 当忘记默认生成的随机密码，可修改默认第一个用户即 admin 密码，如你不输入密码，脚本会自动生成新的16位密码并显示给你。   
`./filebrowser.sh -ls` 可列出当前所有用户；     
`./filebrowser.sh -add xxxx zzzzz` 可新增普通用户，其中 xxxx 为用户名 zzzzz 为密码。注意，密码需要足够复杂，否则会失败报错。   
