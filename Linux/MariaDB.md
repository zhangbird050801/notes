
```shell
proxychains sudo pacman -S mysql
```

选择 1 使用软件仓库 mariadb

```shell
sudo mariadb-install-db --user=mysql --basedir=/usr --datadir=/var/lib/mysql
```

```shell
systemctl status mariadb.service
```

提示输入系统密码，输入即可启动

启动 mysql
```shell
sudo systemctl start mysqld 
sudo systemctl status mysqld
```