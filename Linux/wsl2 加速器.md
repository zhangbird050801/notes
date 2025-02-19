参考文章 -> 这里面有更多的方法
{% link 在 WSL2 中使用 Clash for Windows 代理连接, East Monster's Blog, https://eastmonster.github.io/2022/10/05/clash-config-in-wsl/ %}

打开 `WSL Settings`
![|275](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250218233845005.png)

网络这里将网络模式从 `Nat` 改为 ` Mirrored `
![|650](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250218234446509.png)

这篇文章对于 mirrored 模式有一些简要的说明：
{% link WSL2 的镜像网络模式：带来更流畅的 Linux 开发体验, LittleFish’Blog, https://www.xiaoiluo.com/article/wsl2-network %}

Clash 这里 `允许局域网连接`。同时，记住这个主程序默认端口，一般情况是 `7890`
![|525](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250218234536043.png)


```shell
sudo visudo
```

取消注释这一行
![|650](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250218235458097.png)

nano 编辑器的保存和退出。
截取自 CSDN:
{% link sudo visudo 退出保存, weiyi556, https://blog.csdn.net/weiyi556/article/details/78980139 %}
![|575](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250218235813783.png)


```shell
wget www.google.com 
```

这样就表示成功了。
![|825](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250219000153282.png)

不过，clash 开启代理的情况下如果没成功，可能需要重启一下 wsl2。
可以在 powershell 里面输入，然后重新打来 wsl2
```shell
wsl --shutdown
```