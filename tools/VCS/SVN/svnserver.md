# svnserver

在centos linux下可以通过下面的命令重启svn服务：

```bash
/etc/init.d/svnserve restart
```

启动svn服务器可以使用下面命令：

```
svnserve -d -r=/your svn path
```

-d参数表示以守护进程形式运行-r指定svn数据库的路径。

