执行该指令的时候，
```shell
ssh -t git@github
```

出现报错：
```ad-warning
ssh: Could not resolve hostname github: Temporary failure in name resolution
```

说明可能因为 22 端口被占用，试一下 443 端口：
```shell
ssh -T -p 443 git@ssh.github.com
```

![|750](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250225191624619.png)

此时可以 ssh 成功。

```shell
vi ~/.ssh/config
```

添加
```shell
Host github.com
  Hostname ssh.github.com
  Port 443
```

