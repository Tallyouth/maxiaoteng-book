# 安装

参考: [https://docs.mongodb.com/manual/tutorial/install-mongodb-on-amazon/](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-amazon/)  
可以选择多平台的安装, 本次安装环境: Amazon linux

## yum安装

```
$ sudo nano /etc/yum.repos.d/mongodb-org-4.0.repo
    paste:
        [mongodb-org-4.0]
        name=MongoDB Repository
        baseurl=https://repo.mongodb.org/yum/amazon/2013.03/mongodb-org/4.0/x86_64/
        gpgcheck=1
        enabled=1
        gpgkey=https://www.mongodb.org/static/pgp/server-4.0.asc

$ sudo yum install -y mongodb-org
```

## 运行

```
$ sudo service mongod start  # 启动服务
$ sudo tail /var/log/mongodb/mongod.log   # 验证是否运行
$ sudo chkconfig mongod on  # 将在系统重启后自启

$ sudo service mongod stop  # 停止服务
$ sudo service mongod restart  # 重启服务
```

## 配置

yum安装后的mongdb  
mongod.conf 的位置: /etc/

```
$ sudo nano /etc/mongod.conf

/var/lib/mongod  # 默认存储位置
/var/log/mongodb/mongod.log  # 默认log位置
port: 27017
bindIp: 127.0.0.1  →  0.0.0.0  # 默认只允许本地访问, 修改后对互联网开放
```

# 使用Robo 3T 通过ssh连接mongodb

1. AWS安全组设置, 添加入站端口 27017
2. Robo 3T添加链接, 使用ssh验证



