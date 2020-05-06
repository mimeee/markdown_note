## docker安装

- ##### 安装依赖包 `sudo yum install -y yum-utils device-mapper-persistent-data lvm2 `

- ##### 设置阿里云镜像源 

  ```shell
  sudo yum-config-manager --add-repo https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo 
  
  ```

- ##### 安装 Docker-CE `sudo yum install docker-ce`

- ##### 启动docker 

  ```shell
  # 开机自启
  sudo systemctl enable docker 
  # 启动docker服务  
  sudo systemctl start docker
  
  ```

- ##### 镜像加速配置

  - 国内从 DockerHub 拉取镜像有时会遇到困难，此时可以配置镜像加速器。Docker 官方和国内很多云服务商都提供了国内加速器服务，例如：

    - [网易](https://hub-mirror.c.163.com/): https://hub-mirror.c.163.com
    - [阿里云](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors)
    - [七牛云加速器](https://reg-mirror.qiniu.com): https://reg-mirror.qiniu.com

  - 阿里云获取加速地址

    - 登陆[阿里云](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors)后，左侧菜单选中镜像加速器就可以看到你的专属地址了：

      ![](/Users/mimee/Documents/my-git/markdown_note/阿里云域名申请和环境部署/image/20200416-194059.png)

    - 对于Ubuntu16.04+、Debian8+、CentOS7

      - `vim /etc/docker/daemon.json`

        ```json
        {
          "registry-mirrors":["https://reg-mirror.qiniu.com/"]
        }
        ```

    - 重启服务

      ```shell
      $ sudo systemctl daemon-reload
      $ sudo systemctl restart docker
      ```

      

      

- ##### 查看docker是否安装成功 `docker -v`

- ##### 卸载docker `yum -y remove docker-engine`

  

## Mac docker 安装

- `brew cask install docker` 

##### 

- 参考博客
  - [linux安装docker](https://www.jianshu.com/p/2dae7b13ce2f)
  - [菜鸟](https://www.runoob.com/docker/centos-docker-install.html)