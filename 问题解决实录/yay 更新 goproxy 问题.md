Get "https://proxy.golang.org/golang.org/x/sys/@v/v0.31.0.zip": d  
ial tcp 142.250.196.209:443: i/o timeout

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250501190202648.png)


临时解决：
```shell
export GO111MODULE=on
export GOPROXY=https://goproxy.cn
```