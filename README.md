# QiNiu-Backup-Linux
使用七牛云存储命令行qshell工具备份Linux服务器数据脚本


# 说明

因需求定时备份数据库文件至QiNiu云存储找到官方工具qshell手动备份，
后因需要每天定时所以网上找了一段时间，最后在GitHub和某站找到脚本。
博主的脚本使用后会出现以下提示：
```
Removing leading `/' from member names 
```
故我对其压缩命令进行了修改，为日常使用放置于Github

# 依赖
* qshell [下载](http://devtools.qiniu.com/qshell-v2.0.3.zip)



# 配置
1. 下载七牛qshell工具
2. 配置 AccessKey 和 SecretKey
3. 按照说明修改配置

# 使用
```
./qshell account AccessKey SecretKey
```
使用qiniu官方网站中 个人面板-->密钥管理-->创建密钥 来获得 AccessKey 和 SecretKey

修改 backup.sh 中参数为你自己的参数，都有说明。

# 手动备份
然后改为可执行文件：
```
chmod +x backup.sh #赋予权限
```
运行的时候就输入下面的代码即可：
```
./backup.sh
```
然后通过 cron 来设置定时运行脚本：
```
crontab -e
加入以下代码，:wq 保存
0 5 * * * /bin/bash /root/backup.sh
```

# 定时备份
```
crontab -e
```
加入以下代码，:wq 保存
# 填入以下,每天凌晨5点执行一次备份,这里可以根据需求进行调整
```
0 5 * * * /bin/bash /root/backup.sh
```
# 这里是配置成每月备份一次的设置
```
* * * 1 * /bin/bash /foo/backup.sh
```

# 参考
[使用七牛云备份网站附件和数据库](https://blog.fazero.me/2016/12/17/backup-vps-to-qiniu/)
