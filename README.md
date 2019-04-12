# Docker 命令
service docker start           #启动docker 服务

docker images                  #查看所有镜像

docker run -it [myimages]     #启动镜像，如果没有，会到docker hub上下载

docker stop [containerID|name]     #停止运行镜像

docket kill [containerID|name]     #停止运行镜像

docker start [containerID|name]     #启动运行镜像

docker run -d --restart=always httpd  #启动运行镜像

docker ps  #查看正在运行的镜像

docker tag hello-world hello-world:tag1    #为hello-world镜像打上tag

docker login -u fionaqinchen    #登录到GitHub，密码：1211314917

docker push fionaqinchen/httpd:vtag1     #上传镜像到docker hub上（要先login）

docker pull fionaqinchen/httpd:vtag1      #下载hub上的镜像

docker run -d -p 5000:5000 -v /myregistry:/var/lib/registry registry:2  #在本地创建registry

-d:后台启动容器.

-p 将容器的 5000 端口映射到 Host 的 5000 端口。5000 是 registry 服务端口。

-v 将容器 /var/lib/registry 目录映射到 Host 的 /myregistry，用于存放镜像数据。

docker tag fionaqinchen/httpd:vtag1 registry.example.net:5000/fionaqinchen/httpd:vtag1 
#修改名字，镜像名称由 repository 和 tag 两部分组成。
而 repository 的完整格式为：[registry-host]:[port]/[username]/xxx只有docker hub上的可以省略[registry-host]:[port]

docker run -d my-image /bin/bash -c "while true; do step1; done"    #持续运行docker run -d --restart=always httpd  #发生意外时，自动重启

docker rm [containerID | name]  #删除容器【运行一段时间后清除exit的】
docker rm -v $(docker ps -aq -f status=exited)      #清除所有缓存的exit容器

① docker create 创建的容器处于 Created 状态。
② docker start 将以后台方式启动容器。 docker run 命令实际上是 docker create 和 docker start 的组合。

docker重启
docker 会根据 --restart 的策略判断是否需要重启容器
如果容器执行 docker stop 或docker kill 退出，则不会自动重启

docker启动命令,docker重启命令,docker关闭命令
启动        systemctl start docker
守护进程重启   sudo systemctl daemon-reload
重启docker服务   systemctl restart  docker
重启docker服务  sudo service docker restart
关闭docker   service docker stop   
关闭docker  systemctl stop docke
