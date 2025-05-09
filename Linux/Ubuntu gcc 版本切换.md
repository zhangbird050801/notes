https://www.dedicatedcore.com/blog/install-gcc-compiler-ubuntu/
https://www.http5.cn/index.php/archives/72/

```shell
sudo apt update
```

# 添加 PPA 软件包
```shell
sudo apt install software-properties-common
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt update
```

# 安装 gcc13
```shell
sudo apt install gcc-13 g++-13
```

# gcc11 和 gcc13 多版本管理
```shell
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-11 20 --slave /usr/bin/g++ g++ /usr/bin/g++-11
```

```shell
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-13 20 --slave /usr/bin/g++ g++ /usr/bin/g++-13
```

查看
```shell
sudo update-alternatives --config gcc
```

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250502192759470.png)

可以按下 enter 来保持当前选择，或者输入数字来进行选择。

# 切换版本
```shell
gcc --version 
```

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250502192942604.png)
