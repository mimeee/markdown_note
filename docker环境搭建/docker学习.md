#### Docker基础

- 参考

  - [Docker快速开始与实践](https://juejin.im/post/5e970731e51d4546d4397dd6)

- #### Docker 架构

  ![](./images/QQ20200416-213818.png)

  - **Docker daemon**
- **Client（ Docker客户端）**
  - **Container（容器）**
- **Registry**
  


- #### `docker search <keyword>`：搜索有关于 keyword 的相关镜像，搜索结果有5列

  - NAME:镜像仓库名称。
  - DESCRIPTION:镜像仓库描述。
  - STARS：镜像仓库收藏数，表示该镜像仓库的受欢迎程度，类似于 GitHub的 stars0
  - OFFICAL:表示是否为官方仓库，该列标记为[0K]的镜像均由各软件的官方项目组创建和维护。
  - AUTOMATED：表示是否是自动构建的镜像仓库

  

- ##### `docker pull <image>[:version]`：下载指定镜像

- ##### `docker images` 列出镜像

  - REPOSITORY：镜像所属仓库名称。 
  - TAG:镜像标签。默认是 latest,表示最新。
  - IMAGE ID：镜像 ID，表示镜像唯一标识。 
  - CREATED：镜像创建时间。
  - SIZE: 镜像大小。

  

- ##### `docker rmi <image>` 删除镜像

  - 删除镜像必须保证没有使用该镜像所创建的容器(包括正在运行的容器，和已经创建但被停止的容器；可使用 `docker ps -a`查看全部的容器)

#### Container 基础

- ##### `docker run` 新建并启动一个容器

  - `-d` 表示后台运行
  - `-P` 表示端口随机映射
  - `-p` 表示指定端口映射
    - `-- ip:hostPort:containerPort` 开放容器端口(containerPort)到宿主机端口(hostPort)
    - `-- ip::containerPort`
    - `-- hostPort:containerPort`
    - `-- containerPort`
  - `--net`选项：指定网络模式，该选项有以下可选参数：
    - `--net=bridge`: 默认选项，表示连接到默认的网桥。
    - `--net=host`: 容器使用宿主机的网络
    - `--net=container:NAME-or-ID`：让 Docker 将新建容器的进程放到一个已存在容器的网络栈中，新容器进程有自己的文件系统、进程列表和资源限制，但会和已存在的容器共享 IP 地址和端口等网络资源，两者进程可以直接通过 lo 环回接口通信。
    - `--net=none`：让 Docker 将新容器放到隔离的网络栈中，但是不进行网络配置。之后，用户可以自己进行配置。

- ##### `docker ps` 列出容器

  - CONTAINER_ID：表示容器 ID。
  - IMAGE:表示镜像名称。
  - COMMAND：表示启动容器时运行的命令
  - CREATED：表示容器的创建时间。 
  - STATUS：表示容器运行的状态。UP表示运行中， Exited表示已停止。
  - PORTS:表示容器对外的端口号。
  - NAMES:表示容器名称。该名称默认由 Docker自动生成，也可使用 docker run命令的-name选项自行指定

- ##### `docker stop <container id> [container id]...` 停止容器

- ##### `docker kill <container id>` 强制停止容器

- ##### `docker start <container id>` 启动一个容器(不新建)

- ##### `docker inspect <container id>` 查看容器所有信息

- ##### `docker container logs <container id>` 查看容器日志

- ##### `docker top <container id>` 查看容器里的进程

- ##### `docker exec <container id>` 进入容器

  - `docker exec -it f0b1c8ab3633 /bin/bash`
  - 使用docker exec命令用于进入一个正在运行的docker容器。如果docker run命令运行容器的 时候，没有使用-it参数，就要用这个命令进入容器。一旦进入了容器，就可以在容器的 Shell  执行命令了







