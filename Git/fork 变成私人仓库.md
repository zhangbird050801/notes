```shell
git clone --bare 要fork的仓库地址
```

以 cs144 项目为例子
```shell
git clone --bare https://github.com/CS144/minnow.git   
```

再进入到克隆下来的仓库目录：
```shell
cd minnow.git
```

```shell
git push --mirror 你的私人仓库地址
```