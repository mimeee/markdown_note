## git 的 config 配置

一个 git 仓库，对其生效的配置文件有三个，其权重从大到小分别是 local > global > system；

- local 

  - 本地配置文件，在项目目录中的 `.git/.gitconfig`，只对本仓库有用；

- global

  - 全部配置文件，在用户家目录中 `~/.gitconfig`，针对某个用户的下的所有git仓库；可以在该配置文件中配置各个项目参数；[详情](https://git-scm.com/docs/git-config#_conditional_includes)

    - 例

      - 新建2个配置文件 `.gitconfig.my-git` `.gitconfig.company-git`

        ```shell
        # ~/.gitconfig.company-git
        [user]
                email=aaabbb@xxx.cn
                name=abc
        ```

        ```shell
        # ~/.gitconfig.my-git
        [user]
                email=ccc@xxx.cn
                name=abcddd
        ```

      - 在全局配置中配置

        ```shell
        # ~/.gitconfig
        [core]
                autocrlf = input
                safecrlf = warn
        [alias]
                st = status
                hi = log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
                ad = add .
                
        [includeIf "gitdir:~/Documents/my-git/"]
               path = ~/.gitconfig.my-git
        
        [includeIf "gitdir:~/Documents/company/"]
               path = ~/.gitconfig.company-git
        ```

- system

  - 针对所有用户，所有git仓库

