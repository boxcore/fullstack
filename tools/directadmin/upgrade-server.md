# Directadmin服务升级

1.44.3开心版的Directadmin，其默认安装的php版本为5.3，wordpress程序需要更高的版本，首先进入
```bash
/directadmin/custombuild/
cd /usr/local/directadmin/custombuild/

# 编辑options.conf设置 clean=yes ， php5_ver=5.3
vi options.conf

# 3.然后执行更新并且重启相关服务

./build clean
./build update
./build all y
service httpd restart
```

