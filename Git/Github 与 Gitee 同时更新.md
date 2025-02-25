我使用的是 ssh 的方式，要在 github 和 gitee 账户中同时添加 `~/.ssh/id_rsa.pub` 的内容。

添加 github 仓库 
```shell
git remote add github 仓库ssh地址
```

可以在 gitee 中导入 github 项目。
![|262](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250225195823171.png)

然后会让你的 gitee 账号和 github 账号进行关联，然后就可以导入需要的仓库。
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250225195842181.png)

然后在你本地的仓库位置打开 git bash 
添加 gitee 仓库
```
git remote add gitee 仓库ssh地址
```

```shell
git remote -v
```
![|550](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250225192401283.png)

推送的时候，
```shell
git push github 分支名称
```

```shell
git push gitee 分支名称
```

例如我两个分支都是 main
```shell
git push github main
git push gitee main
```

可以编写自动提交脚本：
```shell
vi push.sh
```

内容如下
```shell
#!/bin/bash
GITHUB_REMOTE="github"
GITEE_REMOTE="gitee"

BRANCH="main"

echo "Pushing to Github..."
git push $GITHUB_REMOTE $BRANCH
if [ $? -eq 0 ]; then
  echo "Successfully pushed to Github."
else
  echo "Failed to push to Github"
fi

echo "Pushing to Gitee"
git push $GITEE_REMOTE $BRANCH
if [ $? -eq 0 ]; then
  echo "Successfully pushed to Gitee."
else
  echo "Failed to push to Gitee."
fi
```

赋予权限
```shell
chmod +x push.sh
```

推送
```shell
./push.sh
```