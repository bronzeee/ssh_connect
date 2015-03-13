git协议连接方式使用的是ssh同服务器通讯，设置ssh走sock5代理连接服务器的同时也解决了git的代理问题。

1.
```
https://raw.githubusercontent.com/bronzeee/ssh_connect/master/connect.c
```

将上述代码使用gcc编译并保存在环境变量目录中同时改名connect
进入.ssh目录新建

文件config
```
Host *
    User git
    ProxyCommand $HOME/.ssh/proxy-wrapper '%h %p'
```

文件 proxy-wrapper
```
#!/bin/bash
~/connect.exe -S http://IP:PORT $@
```
