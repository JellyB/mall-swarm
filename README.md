## SPRINGBOOT LEARNING

### NACOS

#### 下载 nacos

[官网](!https://nacos.io/zh-cn/docs/deployment.html)

#### Nacos部署环境

Nacos定义为一个IDC内部应用组件，并非面向公网环境的产品，建议在内部隔离网络环境中部署，强烈不建议部署在公共网络环境。

以下文档中提及的VIP，网卡等所有网络相关概念均处于内部网络环境。

#### Nacos支持三种部署模式

- 单机模式 - 用于测试和单机试用。
- 集群模式 - 用于生产环境，确保高可用。
- 多集群模式 - 用于多数据中心场景。
#### 环境准备

安装好 JDK，需要 1.8 及其以上版本
建议: 2核 CPU / 4G 内存 及其以上
建议: 生产环境 3 个节点 及其以上

#### 单机模式下运行Nacos

#### Linux/Unix/Mac

Standalone means it is non-cluster Mode.

start up mysql

```bash
cd /usr/local/Cellar/mysql@5.6/5.6.50/bin
./mysql.server start
```

```bash
cd ~/Documents/workspace/github/nacos/bin
$ sh startup.sh -m standalone
```

#### Windows

Standalone means it is non-cluster Mode.

```bash
$ cmd startup.cmd -m standalone
```

[首页](!http://localhost:8848/nacos/#/login)

```conf
username: nacos
password: nacos
```

#### 单机模式支持mysql

在0.7版本之前，在单机模式时nacos使用嵌入式数据库实现数据的存储，不方便观察数据存储的基本情况。0.7版本增加了支持mysql数据源能力，具体的操作步骤：

1.安装数据库，版本要求：5.6.5+
2.初始化mysql数据库，数据库初始化文件：mysql-schema.sql
3.修改conf/application.properties文件，增加支持mysql数据源配置（目前只支持mysql），添加mysql数据源的url、用户名和密码。

```conf
db.num=1
spring.datasource.platform=mysql

db.url.0=jdbc:mysql://localhost:3306/test?characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true
db.user=nacos_devtest
db.password=youdontknow
```

再以单机模式启动nacos，nacos所有写嵌入式数据库的数据都写到了mysql


[集群模式下运行Nacos](!https://nacos.io/zh-cn/docs/cluster-mode-quick-start.html)

## 启动redis

```bash
cd /usr/local/Cellar/redis/5.0.7/bin
./redis-server
```

## 启动 mall-auth-application

## 启动 mall-gateway-application

## 启动 mall-admin-application
