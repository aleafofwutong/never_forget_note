# git 的使用方法

> 一些说明：
> git 流程结构：

```mermaid
graph TD
    linkStyle default interpolate - monotone
    A[工作区<br>Working Directory] -->|git add 文件名 / git add .| B[暂存区<br>Staging Area/Index]
    B -->|git commit -m '提交说明'| C[本地仓库<br>Local Repository<br>]
    C -->|git push 远程别名 分支名| D[远程仓库<br>Remote Repository<br>（GitHub/GitLab等）]
    
    D -->|git fetch 远程别名| C
    D -->|git pull 远程别名 分支名| A 
    C -->|git checkout 分支名 / git switch 分支名| A 
    
    %% 辅助操作
    A -->|git restore 文件名| A 
    B -->|git restore --staged 文件名| A
    C -->|git reset --hard 提交哈希| A
    C -->|git branch 新分支名| C
    C -->|git merge 分支名| C
    
    %% 样式标注
    style A fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    style B fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
    style C fill:#ff0000,stroke:#fb5e20,stroke-width:2px
    style D fill:#fff3e0,stroke:#e65100,stroke-width:2px
```


## 初始化
```bash
    git init #初始化一个git仓库
```
## 查询状态
```bash
    git status # 查询git仓库状态
    git branch (-v) # 查询分支状态
    git remote -v #查询远程连接
```
## 配置
```bash
    git config --global user.name "your_name"
    git conig --global user.email "xxx@xxx.com" 
```


## **关联github仓库**
```bash
    git remote add <local_branch_name> <http://...>
```
* ATTENTION

    > 此处的local_branch_name仅在执行这个命令的电脑上可用

    > 而remote repositories仍然是master(git默认)或main(github默认) 

        真正改名：
    ```bash
        git branch -M <new_name> # 重命名
    ```
        或
        ` git checkout -b <new_name> `
        ` git branch -D <old_name> `

最后
```bash
`git push <local_branch_name> <new_name> -u
```
## 添加
```bash
git add <file>
git commit (-m "msg")
git push <local_branch_name> 
```

## 拉取

```bash
git fetch
git merge
git pull
```