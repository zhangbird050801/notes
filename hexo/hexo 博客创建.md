# 安装 hexo 
前提条件是必需安装了 nodejs。

安装 hexo，命令行 (推荐用 git bash) 输入：
```shell
npm install hexo-cli -g
```

# 初始化博客
初始化博客，myblog 可以替换成你想要的文件夹名字。
```shell
hexo init myblog
```

![|550](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216220049007.png)


```shell
cd myblog 
npm install
```

启动本地预览：
注意这个 hexo s 就是开启本地预览，如果你关了之后就看不到了
```shell
hexo clean
hexo g
hexo s
```

进入博客：
{% link 博客, hexo, http://localhost:4000/ %}

显示以下界面即表示成功，这是在本地部署成功。
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216220426830.png)

# GitHub 部署
先安装必要的插件：
```shell
npm install hexo-deployer-git --save
```

## 新建仓库
打开你个人的 github 仓库主页，新建仓库，我这里使用小号演示。
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216220216159.png)

仓库名 `.github.io` 前面必须和你的 github 用户名一致。
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216220311032.png)

选择复制 ssh 的地址，最好不要用 http 的。
后面我会演示如何配置 ssh

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221058387.png)

## 配置博客
下面有单账户配置和多账户配置，多账户配置适合于你本地有两个 github 账户，然后你想指定某个 hexo 仓库用到指定的 github 账户的话，你可以看看我的多账户配置。
当然，一般都是单账户，所以直接看单账户就好了。
### 单账户配置
博客根目录下的 `_config.yml` 里面配置 github url，这里用的是 `https://你的用户名.github.io`
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216222442336.png)

也是在 `_config.yml` 最底下找到：
repository 就是前面新建仓库之后的 ssh 地址。
branch 和你仓库默认对应就行，但是我建议改成 main。
```yml
deploy:
    type: git
    repository: git@github.com:BouncyEly/BouncyEly.github.io.git
    branch: main
```

如果不用配置多账户，完成这里之后跳到 配置 ssh 模块。

### 多账户配置 (可以跳过)
也可以用以下配置 (因为我有多个账户，所以我局部配置了一下 git)
```yml
deploy:
    type: git
    repository: git@BouncyEly.github.com:BouncyEly/BouncyEly.github.io.git
    branch: main
    name: BouncyEly
    email: 1516024203@qq.com
```

我这里配置了两个 ssh，分别属于我两个 github 账户：
`C:\Users\Birdy\.ssh\config`

![|525](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216224655343.png)

在博客 `.deploy_git/.git` 目录下找到 config
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216224949262.png)

在里面加上：
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216225018271.png)

```
[user]
	name = BouncyEly
	email = 1516024203@qq.com
```


## 配置 ssh
刚才配置完之后 `_config.yml` 底下是这样的。
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221150575.png)

然后我们配置一下 ssh。

也可以看我另一篇文章

{% link 博客, Github | 配置SSH , https://birdyweb.top/post/790c8b8.html %}

git bash 打开：
有个 enter file 的提示，提示你保存到哪里，你可以直接按 enter 就是保存到默认路径
`C:\Users\用户名\.ssh\`，但是我这里自己指定了一下，
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221505387.png)

```shell
ssh-keygen -t rsa -b 4096 -C "你的github用户邮箱" 
```

比如我的：
```shell
ssh-keygen -t rsa -b 4096 -C "1516024203@qq.com" 
```

然后在 `C:\Users\用户名\.ssh\` 路径下，找到 `id_rsa.pub` 文件，用记事本之类的打开，待会需要用到
![|675](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221532094.png)

### Github 配置 ssh
github 页面打开 settings
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221620252.png)

点击 `New SSH key`，我们将要注册前面生成的 ssh key
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221640830.png)


复制 id_rsa.pub 里面的内容
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216222009694.png)

粘贴到这里面。
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221848691.png)

提交。
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216222028056.png)

### 配置本地 git 账户
单用户直接配置全局的:
```shell
git config --global user.name "userName"       //你的用户名
git config --global user.email "email address" //你的邮箱地址
```

测试能否正常 ssh 连接。输入完下面这个之后可能会有提示你保存什么东西的，你输入 `yes` 就可以
```shell
ssh -T git@github.com
```

### 部署 hexo 
```shell
hexo clean
hexo g
hexo d
```

然后尝试访问 `https://你的用户名.github.io`

比如我这个：

{% link 博客, BouncyEly 的 hexo 博客 , https://bouncyely.github.io/ %}

-> 访问不出来 `ctrl + F5` 多刷新几次

# 安装主题
你也可以用别的主题, hexo 官网提供了很多。

安装主题 https://docs.anheyu.com/initall.html

在你的博客 **根目录** 下，打开 git bash 输入。
```shell
git clone -b main https://github.com/anzhiyu-c/hexo-theme-anzhiyu.git themes/anzhiyu
```

然后找到刚才克隆下来的文件夹
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216225247009.png)

将博客根目录下的 `_config.yml` 文件里面的 theme 改为 `anzhiyu`
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216225321079.png)


打开 git bash 安装插件
```shell
npm install hexo-renderer-pug hexo-renderer-stylus --save
```

将主题文件（`themes/anzhiyu` ）下的 `_config.yml` 复制一份，名字改为 `_config.anzhiyu.yml` 放到博客根目录下

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216225445914.png)

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216225553360.png)

最后再重新部署一下：
```shell
hexo clean
hexo g
hexo d
```

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216230001915.png)


本地预览：
```shell
hexo s 
```

加载不出来 ctrl + F5 刷新！多刷新几次。效果就可以呈现出来了！

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216230145876.png)
