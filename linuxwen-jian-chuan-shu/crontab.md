# Cron

## 命令的使用

1. 列出当前任务	
    crontab -l 
2. 备份当前任务列表	
    crontab -l > my_cron   
3. 编辑一个命令文件      
    nano my_crontab
4. 将编辑好的命令生效  
    crontab my_crontab 
5. 重启crond
    service crond restart


## 命令格式
	
```
# 文件格式说明
#  ——分钟（0 - 59）
# |  ——小时（0 - 23）
# | |  ——日（1 - 31）
# | | |  ——月（1 - 12）
# | | | |  ——星期（0 - 7，星期日=0或7）
# | | | | |
# * * * * * 被执行的命令
```
- 命令用空格分隔， 
- 不用的, 任意可能的使用*代替
- 多个值用','分割

## 不发送电子邮件

如果输出结果来自crontab, 那么cron守护进程会使用电子邮件发送给用户, 位置```/var/spool/mail/ec2-user```, 需要将命令重定向到 ```>dev/null 2>&1```

## 查看日志排除问题

位置: ```/var/log/cron```

## crontab设置scrapy脚本的定时任务

编写shell脚本

```
#!/bin/sh
. ~/.bash_profile
# 切换到scrpay命令下
cd /home/ec2-user/crawler/mangoplate_scrapy/

# 依次启动爬虫
/usr/local/bin/scrapy list
/usr/local/bin/scrapy crawl codetable
/usr/local/bin/scrapy crawl mangoplate

# 去重
/usr/bin/python3 deduplicate.py
```