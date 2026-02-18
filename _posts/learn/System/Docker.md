---
title: 【Docker】Docker 学习与记录
tags:
- Docker
categories:
- 学习
- 操作系统
---


# Docker 学习与记录

## Docker 是啥

> Docker 官网：[Docker](https://www.docker.com/)
>
> 参考资料：[Docker 菜鸟教程](https://www.runoob.com/docker/docker-tutorial.html)

~~删除第一次，原样的复制黏贴。~~

~~删除第二次，在第一次的基础上调整为QA的方式，但感觉有点小题大作了。~~

目前为止，我的实际需求是会用就行，以及了解一些关键概念。所以第一步，是粗读一遍，然后记录关键词即可。包含目录结构之类的，略过。

容器（Container），镜像（Image），仓库（Registry），Dockerfile

```
docker ps
CONTAINER ID: 容器 ID。
IMAGE: 使用的镜像。
COMMAND: 启动容器时运行的命令。
CREATED: 容器的创建时间。
STATUS: 容器状态。
    created（已创建）
    restarting（重启中）
    running 或 Up（运行中）
    removing（迁移中）
    paused（暂停）
    exited（停止）
    dead（死亡）
PORTS: 容器的端口信息和使用的连接类型（tcp\udp）。
NAMES: 自动分配的容器名称。
```

容器互联

Dockerfile，镜像构建

Compose，多容器应用构建

Machine，管理多服务器上的 Docker 服务

Swarm，管理多个服务器上的 Docker 容器

## 如何使用

先去[https://hub.docker.com/](https://hub.docker.com/)上找自己想要的镜像，然后通过**docker-compose**配置启动

## 安装

首先可用`which docker`查看本地是否已经安装Docker

之后根据[菜鸟教程](https://www.runoob.com/docker/ubuntu-docker-install.html)里的说明进行安装

``` shell
# 使用官方安装脚本自动安装
curl -fsSL https://test.docker.com -o test-docker.sh	# 可能会有点慢，卡在那里
sudo sh test-docker.sh
```

## 安装docker-compose

### 安装

docker-compose的说明可以看[菜鸟教程](https://www.runoob.com/docker/docker-compose.html)，个人理解，有点像是容器的集群，来共同实现一个的服务。

首先从[Github](https://github.com/docker/compose/releases)上可以找到最新的版本，然后通过curl下载

```shell
# 下载
sudo curl -L "https://github.com/docker/compose/releases/download/v2.26.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
# 赋予可执行权限
sudo chmod +x /usr/local/bin/docker-compose
# 创建软连接（todo 可以看下软链接这个是干啥用的）
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

### 配置文件说明

创建`docker-compose.yml`

 ```yaml
 version: '3'
 services:	# 容器列表
   app:		# 容器1名
     image: 'jc21/nginx-proxy-manager:latest'	# 容器镜像，不推荐:latest
     restart: unless-stopped						# 重启策略
     ports:										# 端口映射
       - '80:80'
       - '81:81'
       - '443:443'
     volumes:									# 目录映射
       - ./data:/data
       - ./letsencrypt:/etc/letsencrypt
 ```

之后，如果文件名不为`docker-compose.yml`，需要另外`-f`指定

```shell
docker-compose down		# 下线
docker-compose pull		# 拉取latest镜像
docker-compose up -d	# 重新上线
```

## 其他

### 修改Docker镜像源

>  参考：[docker 修改使用国内镜像源](https://www.jianshu.com/p/dfd30e94b517)

```shell
# 修改daemon.json文件，如果没有先建一个即可
sudo vim /etc/docker/daemon.json
# reload docker
sudo systemctl daemon-reload
sudo systemctl restart docker 
# 检查配置是否生效
sudo docker info|less
# 检索一下应用
sudo docker search nginx
```

daemon.json 改成

```json
{
  "registry-mirrors": ["https://docker.mirrors.ustc.edu.cn"],
  "log-driver":"json-file",
  "log-opts": {"max-size":"100m", "max-file":"3"}
}
```

其他的镜像源：

- 阿里云：https://registry.cn-hangzhou.aliyuncs.com
- docker中国：https://registry.docker-cn.com
- 网易：http://hub-mirror.c.163.com
- 腾讯云：https://mirror.ccs.tencentyun.com

### Docker日志管理（TODO）

> 参考：[限制Docker容器日志大小+清理日志脚本](https://sleele.com/2019/06/13/限制docker容器日志大小清理日志脚本/)

TODO 待定

### 添加非root用户到docker用户组（TODO）

TODO 待定

## 服务相关

### ddns-go

这个得从DNS的概念聊起了。DNS(Domain Name System)，域名系统

实时抓取当前的公网ip，然后同步到域名服务商的DNS中

VPS因为已经固定分配了一个公网的ip4，所以倒是不必要

### NPM

Nginx proxy manager，nginx的反向代理工具，同时也是nginx的可视化管理工具，默认端口81

`docker-compose.yml`

```yaml
version: '3'
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      - '80:80'
      - '<NPM-后台端口>:81'
      - '443:443'
    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
```

之后，通过`http://<服务器ip>:<NPM-后台端口>`进行访问，默认用户密码为：

```
默认帐户：admin@example.com
默认密码：changeme
```

#### 域名-证书

关于域名，可以在阿里云或者其他服务商那里购买域名。不过测试期间可以先直接用ip访问将就下，但安全起见还是上域名了。

之后证书，也就是ssl，`Secure Sockets Layer`，简单来说就是https中的s。一般在域名服务商都会提供证书申请服务，不过虽然我的域名是在阿里云上购买的，但目前阿里云的免费证书只有单域名的，所以另外选择了从cloudflare上申请证书。步骤如下：

先将当前的证书录入cloudflare，并且将阿里云上证书的dns配置为cloudflare提供的地址，这里不需要完全将证书从阿里云迁移到cloudflare上。

之后获取cloudflare的`api 令牌`，之间默认操作即可，之后获取到一个token，记下。

![chrome_1oD1dhrvOm](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/04/19-c91c6531fecf6fa18e120b2870ed065a-chrome_1oD1dhrvOm.webp)

再到npm这边，通过`SSL Certificates`添加令牌，申请证书。这里的**Let's Encrypt**是个证书颁发机构。

![chrome_fMLvfgPAfY](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/04/19-8c1c72cfa653c10dccb75327a8ff14e6-chrome_fMLvfgPAfY.webp)

上面是要申请的域名地址，下面的是你从cloudflare记下的token，之后save，等待一会就申请下来了。

![chrome_JeyneXfoel](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/04/19-5d15795a1f45c42f1bd735330435b4d5-chrome_JeyneXfoel.webp)

之后就可以到npm中添加反向代理的地址了。

![chrome_0S0OVR6KVl](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/04/19-54e79d0ec28468171f2d19d7aeec17d0-chrome_0S0OVR6KVl.webp)

![chrome_1x1XRgqlzy](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/04/19-847a980d3432e189735ba4e422984963-chrome_1x1XRgqlzy.webp)

#### 错误：将您重定向的次数过多

在使用cloudflare时会出现，修改如下。

![chrome_iJAWxoYDiR](https://byyw-oss1.oss-cn-hangzhou.aliyuncs.com/img/2024/04/19-5df10897f011f0cf047350edb443cef8-chrome_iJAWxoYDiR.webp)

### Portainer

docker 管理工具

```shell
# 提前拉取镜像
docker pull portainer/portainer-ce
 
# 开放目标端口，我们这里用9000。你应该改一个别的端口。
sudo ufw allow 9000 comment 'portainer' && sudo ufw reload
 
# 安装Portainer
docker run -d \
    --restart=unless-stopped \
    -p 9000:9000 `#改自己喜欢的端口号` \
    -v /var/run/docker.sock:/var/run/docker.sock \
    --name portainer \
    portainer/portainer-ce

```

### Rclone

这是个备份工具，TODO 待定

## Docker Desktop

Windows 下的 Docker 管理工具，依赖 WSL （运行在 Windows 下的 Linux 子系统）

- 下载的 images 位置在哪

  新版本（29.1.3）存放在自定义位置（setting - Resources - Disk image location），默认在 C，改到 E 了。

  找的了位置，但是看不了，神烦。

  又似乎不对，是否需要放弃docker desktop，只玩 docker。

  行吧，暂时忽视这个问题。而对于 docker 的使用，还是原教旨主义的基于命令行与文件进行。

- 自低向上

  基础镜像 （docker pull 拉取）

  dockerfile 额外依赖 应用程序

  docker build [dockerfile] 得到容器镜像

  docker register （docker push/pull）镜像仓库 推拉容器镜像

  docker run [容器镜像] 得到运行的容器

  周边

  - docker compose

    docker-compose up 按自定的 yaml 配置文件部署多容器，实现一套服务

  - docker swarm / k8s 

    一套服务在多服务器的集群部署

  行了，到此为止，不要因小失大，关注我的主要意图，是安装 mysql
