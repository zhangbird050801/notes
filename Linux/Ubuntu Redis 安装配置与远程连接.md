
首先就是安装东西前必备的：
```shell
sudo apt update
sudo apt upgrade
```

## 安装 redis
```shell
sudo apt install redis-server
```

## 查看 redis 版本
```shell
redis-cli --version
```

## 启动与关闭 redis
### 启动 redis
这种挂在后台启动：
```shell
systemctl start redis
```

也可以用，不过这种是前台运行
```shell
redis-server
```
这种 Ctrl + C 退出后进程会被关掉，不过可以通过修改配置以及启动时在后面指定配置路径来解决。
![|650](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250210220555391.png)

### 关闭 redis
```shell
sudo systemctl stop redis
```

## 查看 redis 运行状态
```shell
systemctl status redis
```

```shell
ps aux | grep redis
```

## 配置 redis
打开 redis 配置文件：
```shell
sudo vim /etc/redis/redis.conf
```

### 允许远程控制
注释掉 `bind 127.0.0.1 :: 1`
![|650](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250210212656685.png)

添加一行 (允许所有主机 IP 访问 -> 测试环境用)
```
bind 0.0.0.0
```

### 密码配置
找到 `requirepass foobared` 这一行
![|650](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250210212948487.png)
取消注释并改成:
```
requirepass <你想要的密码>
```

### daemonize 配置
```ad-cite
- `daemonize:yes`: redis 采用的是单进程多线程的模式。当 redis.conf 中选项 daemonize 设置成 yes 时，代表开启守护进程模式。在该模式下，redis 会在后台运行，并将进程 pid 号写入至 redis.conf 选项 pidfile 设置的文件中，此时 redis 将一直运行，除非手动 kill 该进程。
- `daemonize:no`: 当daemonize选项设置成no时，当前界面将进入 redis 的命令行界面，exit 强制退出或者关闭连接工具(putty,xshell等)都会导致redis 进程退出。
```

![|650](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250210215815628.png)

我们选择 daemonize 设置为 yes。

保存配置文件之后，重新启动 redis 服务。
```shell
systemctl restart redis-server
```

我们再看看 redis 进程状态：可以看到最后面是 0.0.0.0:6379
```shell
ps aux | grep redis
```
![|650](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250210215209007.png)

## 远程连接
### 使用 vscode 插件连接
Vscode 提供插件，可以用这个来连接。
![|440](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250210220359402.png)

把主机名改了，以及密码，再连接。
![|500](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250210213240435.png)

连接成功后：
![|518](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250210220726614.png)

### 使用本地 redis-cli
在 redis 安装包下有个 `redis-cli. exe` 文件。在这个目录下右键，选择在终端打开。

![|550](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250210221240973.png)

输入指令
```shell
.\redis-cli.exe -h <你的 linux 主机 IP> -p 6379 -a <你在配置文件中设置的 redis 连接密码>
```
比如我这个：
![|600](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250210221438095.png)
