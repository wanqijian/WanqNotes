# CentOS 环境配置

Yum（全称为 Yellow dog Updater, Modified）是一个在Fedora和RedHat以及CentOS中的Shell前端软件包管理器。基于RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软件包，无须繁琐地一次次下载、安装。


**更新 yum**

```bash
yum update -y
```

**Java 环境**

```bash
# 下载工具 wget
yum install wget

# 先去 Oracle 网站确定 JDK 的下载链接
# 下载 Oracle JDK
wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u181-b13/96a7b8442fe848ef90c96a2fad6ed6d1/jdk-8u181-linux-x64.tar.gz


mkdir /usr/java
cp jdk-8u181-linux-x64.tar.gz /usr/java
cd /usr/java
tar -zxvf jdk-8u181-linux-x64.tar.gz

vi ~/.bash_profile
# 设置 java 的环境变量
export JAVA_HOME=/usr/java/jdk1.8.0_181
export CLASSPATH=.:${JAVA_HOME}/jre/lib/rt.jar:${JAVA_HOME}/lib/dt.jar:${JAVA_HOME}/lib/tools.jar
export PATH=$PATH:${JAVA_HOME}/bin

# 执行修改的文件
source ~/.bash_profile

# 测试
java
javac

```

**Nginx**
```bash
# 安装 nginx
yum install nginx

# 启动 nginx
nginx

# 检查 conf 文件
nginx -t

# 重启
nginx -s reload

```

**SSL-acme.sh**

[ACME](https://github.com/Neilpang/acme.sh)

```bash
# 安装 acme
curl  https://get.acme.sh | sh

# 安装在 ~/.acme.sh 文件夹
# 通过 dns 方式
export DP_Id="dnspod id"
export DP_Key="dnspod key"
acme.sh --issue --dns dns_dp -d *.your-site -d your-site

```
**安装 nvm**

```bash
# 安装
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash

# 添加以下脚本只 bash profile
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion


```


