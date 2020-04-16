### 配置多账户ssh

- 生成ssh

  - `ssh-keygen -t rsa -C "email@company.com" -f ~/.ssh/id_rsa_company`

    - 该命令是生成一个邮箱为 `email@company.com` 的公密钥，文件名为 `id_rsa_company`

  - 设置 config

    - `vim ~/.ssh/config` 编辑配置文件

      ```shell
      # 配置文件参数
      # Host : Host可以看作是一个你要识别的模式，对识别的模式，进行配置对应的的主机名和ssh文件（可以直接填写ip地址）
      # HostName : 要登录主机的主机名（建议与Host一致）
      # User : 登录名（如gitlab的username）
      # IdentityFile : 指明上面User对应的identityFile路径
      # Port: 端口号（如果不是默认22号端口则需要指定）
      
      # gitlab
      Host github.com
      Port 22
      HostName github.com
      PreferredAuthentications publickey
      IdentityFile C:/Users/xiaohaozi/.ssh/id_rsa_github
      User aaa
       
      # gitlab
      Host gitlab
      Hostname gitlab.conpany.cn
      PreferredAuthentications publickey
      IdentityFile ~/.ssh/id_rsa_company
      User aaa
      
      ```

    - 其他ssh命令

      - `ssh-agent bash`
      - `ssh-add ~/.ssh/id_rsa $ ssh-add ~/.ssh/github_rsa` 添加私钥
      - `ssh-add -l` 查看私钥列表
      - `ssh-add -D` 清空私钥列表
      - `ssh -T git@github.com` 测试

- 参考博客：
  - [Git配置多个SSH key](https://blog.csdn.net/hao495430759/article/details/80673568)