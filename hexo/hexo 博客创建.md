
安装 hexo
```shell
npm install hexo-cli -g
```


```shell
hexo init myblog
```

![|550](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216220049007.png)



```shell
cd myblog 
npm install
```

```shell
hexo clean
hexo g
hexo s
```

进入博客：
{% link 博客, hexo, http://localhost:4000/ %}


![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216220426830.png)







```shell
npm install hexo-deployer-git --save
```

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216220216159.png)


![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216220311032.png)

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221058387.png)






![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216222442336.png)


```shell
deploy:
    type: git
    repository: git@github.com:BouncyEly/BouncyEly.github.io.git
    branch: main
```

也可以用以下配置 (因为我有多个账户，所以我局部配置了一下 git)
```shell
deploy:
    type: git
    repository: git@BouncyEly.github.com:BouncyEly/BouncyEly.github.io.git
    branch: main
    name: BouncyEly
    email: 1516024203@qq.com
```

`C:\Users\Birdy\.ssh\config`

![|525](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216224655343.png)

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216224949262.png)

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216225018271.png)

```
[user]
	name = BouncyEly
	email = 1516024203@qq.com
```


![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221150575.png)



![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221505387.png)
```shell
ssh-keygen -t rsa -b 4096 -C "1516024203@qq.com" 
```


![|675](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221532094.png)


![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221620252.png)


![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221640830.png)


复制 id_rsa.pub 里面的内容

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216222009694.png)




![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216221848691.png)


![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216222028056.png)


```shell
git config user.name "userName"       //你的用户名
git config user.email "email address" //你的邮箱地址
```


```shell
ssh -T git@username.github.com`
```


```shell
hexo clean
hexo g
hexo d
```


https://bouncyely.github.io/   即可正常访问  -> 访问不出来 `ctrl + F5` 多刷新几次



安装主题 https://docs.anheyu.com/initall.html

```shell
git clone -b main https://github.com/anzhiyu-c/hexo-theme-anzhiyu.git themes/anzhiyu
```


![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216225247009.png)

`_config.yml` 文件 theme 改为 `anzhiyu`

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216225321079.png)


安装插件
```shell
npm install hexo-renderer-pug hexo-renderer-stylus --save
```

将主题文件下的 `_config.yml` 复制一份，名字改为 `_config.anzhiyu.yml` 放到博客根目录下

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216225445914.png)




![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250216225553360.png)


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
