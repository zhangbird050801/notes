windows 版地址：https://www.minio.org.cn/download.shtml#/windows
(内有 Docker、Linux、macOs 等版本下载方式)
以下内容为 windows 版本

安装：
1、先获取 minio 的 Server 端 和 Client 端文件
2、手动创建文件夹 minio 及其子文件夹 bin、data、logs
3、将服务端与客户端文件放入 bin 文件夹内
4、在 bin 文件夹内打开命令行
```shell
setx MINIO_ROOT_USER name 			//name 改为自定义用户名
setx MINIO_ROOT_PASSWORD password	//password 改为自定义密码
```

注：用户名需大于 3 位，密码需大于 8 位
输入完关闭命令行

启动：
在 bin 目录下打开命令行输入
```java
.\minio. exe server D:\Minio\data --console-address "127.0.0.1:19000" --address "127.0.0.1:19001" > D:\Minio\logs\minio. log 2>&1
```
(目录及 ip 端口根据需求更改，第一个目录为文件保存目录， 第二个目录为日志保存目录)
可启动 minio 并通过 127.0.0.1:19000 端口访问界面

注：
1、若 ip 设为 127.0.0.1:19000 则只有本机能访问到，推荐设置为 : 19000，这样可通过本机 ip 访问
2、190001 为数据访问端口，查看文件和调用 api 端口都是通过该端口访问
3、minio 中桶的权限建议设置为 public，以方便查看文件
4、在并目录下可新建. bat 脚本文件快速启动 Minio，内容为
```shell
if "%1"=="hide" goto CmdBegin
start mshta vbscript: createobject ("wscript. shell"). run ("""%~0"" hide", 0)(window. close)&&exit
:CmdBegin
.\minio. exe server D:\Minio\data --console-address ": 19000" --address ": 19001" > D:\Minio\logs\minio. log 2>&1
```

```shell
@echo off
title MinIO Server
echo Starting MinIO Server...

:: 创建日志目录（如果不存在）
if not exist "D:\Minio\logs\" mkdir "D:\Minio\logs"

:: 设置环境变量（可选）
set MINIO_ROOT_USER=admin
set MINIO_ROOT_PASSWORD=password

:: 运行MinIO服务器
.\minio.exe server D:\Minio\data --console-address "127.0.0.1:19000" --address "127.0.0.1:19001" > D:\Minio\logs\minio.log 2>&1

:: 保持窗口打开以便查看可能的错误
pause
```

http://127.0.0.1:19000/browser