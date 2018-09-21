# Deploy with external (MySQL)database

在一些特殊情况下，我们可能希望单独部署数据库，例如为了得到更高的数据库性能或多机高可用特性。

## 部署数据库

1. 安装部署mysql
2. 为mysql创建新的用户，例如guacamole并配置密码(目前必须配置密码)
3. 为该用户设置访问授权
4. 创建guacamole数据库
5. 将initdb.sql导入数据库

```bash
## 创建用户
mysql> use mysql;

mysql> CREATE USER 'guacamole'@'%' IDENTIFIED BY 'user';

mysql> GRANT ALL ON *.* TO guacamole@'%' identified by 'user';

## 创建数据库
mysql -u guacamole -p user;
mysql> create database guacamole;

## 导入数据库
mysql -u guacamole -p user guacamole < initdb.sql
```

6. 编辑.env环境变量，保证数据库相关环境变量和你设置的一致。