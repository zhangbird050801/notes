ssh: Could not resolve hostname ssh. github. com: Temporary failure in name resolution

```shell
sudo vim /etc/wsl.conf
```

防止 wsl2 重启 DNS 配置消失：
```shell
#[boot]
#systemd=true
[network]
generateResolvConf = false
```

```shell
sudo vim /etc/resolv.conf
```

```shell
nameserver 8.8.8.8
nameserver 1.1.1.1
```

powershell 内重启 wsl2
```shell
wsl.exe --shutdown
```

重新打开 wsl2 之后 ssh 测试
```shell
ssh -T git@github.com 
```

此时一切正常：
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250502162049716.png)

