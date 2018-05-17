# Sniperoj Dockerfile

#### Description
* Platform Source Code: https://github.com/SniperOJ/SniperOJ-Platform
* Writeups of Challenges: https://github.com/SniperOJ/SniperOJ-Challenge-Writeups

```
本仓库主要存储了 SniperOJ 训练平台的所有题目需要用到的 Docker 环境的 Dockerfile
初衷是为了能让 CTFer 们能够在本地快速搭建题目运行环境
集成管理比较方便
而且希望以后能将 SniperOJ 做成一个可以自动化部署监控题目运行情况的平台
Fight
```

```
所有题目的镜像也都 push 到了 Dockerhub 上
链接如下 : 
https://hub.docker.com/r/wangyihang/sniperoj/
```

Dockerfile 使用方法 : 
---
```
1. 安装 Docker
apt install docker.io
2. clone 仓库
git clone https://github.com/SniperOJ/Dockerfile.git
3. 进入某一个想要搭建的题目文件夹中 , 例如 pwn/pwn350-leak-advanced-x86-64
cd ./Dockerfile/pwn/pwn350-leak-advanced-x86-64
4. 构建镜像
docker build -t 'pwn350-leak-advanced-x86-64' .
5. 运行容器
WEB题目
docker run -i -d -p 8080:80 -p 127.0.0.1:8081:22 --name 'challenge_name' [IMAGE_NAME] /run.sh
PWN题目
docker run -i -d -p 8080:65535 -p 127.0.0.1:8081:22 --name 'challenge_name' [IMAGE_NAME] /run.sh
```

Docker 镜像的使用方法
---
```
1. 首先安装 Docker
apt update && \
apt upgrade -y && \
apt dist-upgrade -y && \
apt install docker.io
2. 将目标镜像拉取到本地
docker pull wangyihang/sniperoj:web50-as-fast-as-you-can
3. 运行镜像
docker run -i -d \
-p 8080:80 -p 8081:22 \
wangyihang/sniperoj:web50-as-fast-as-you-can \
/run.sh
4. 成功启动容器后
打开浏览器访问 : http://localhost:8080 即可
5. 如何访问 Docker
通过 ssh 连接 docker 即可 , 默认不支持 root 用户登录
存在 sniper 用户 , 密码为 sniperoj
root 用户密码也为 sniperoj
但是 sniper 不是 sudoer , 需要通过 su 命令切换到 root 用户
```



目前已经通过测试的 Dockerfile 如下 : 
---
- [x] pwn350-leak-advanced-x86-64


