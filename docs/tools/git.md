# Git 版本控制

## 概述
Git 是一个分布式版本控制系统，用于跟踪文件的变化并协调多人开发工作。

## 核心概念
```mermaid
graph LR
    WorkDir[Working Directory] --> Stage[Staging Area]
    Stage --> Local[Local Repository]
    Local --> Remote[Remote Repository]
```

## 基本命令
```bash
# 仓库初始化
git init

# 添加文件
git add <file>
git add .

# 提交更改
git commit -m "message"

# 查看状态
git status
```

## 分支管理
```bash
# 创建分支
git branch feature

# 切换分支
git checkout feature
# 或
git switch feature

# 合并分支
git merge feature
```

## 远程操作
1. 克隆仓库
   ```bash
   git clone <url>
   ```

2. 推送更改
   ```bash
   git push origin main
   ```

3. 拉取更新
   ```bash
   git pull origin main
   ```

## 常用工作流

### Feature Branch Workflow
1. 创建特性分支
2. 开发新功能
3. 提交更改
4. 合并到主分支

### GitFlow
1. Master分支
2. Develop分支
3. Feature分支
4. Release分支
5. Hotfix分支

## 最佳实践
1. 提交信息
   - 使用清晰的描述
   - 遵循约定格式
   - 关联问题编号

2. 分支策略
   - 定期同步主分支
   - 及时删除已合并分支
   - 遵循分支命名规范

3. 代码审查
   - 创建Pull Request
   - 进行Code Review
   - 处理反馈意见

## 高级特性
1. Git Hooks
2. Submodules
3. Cherry-pick
4. Rebase
5. Stash

## 故障排除
1. 冲突解决
2. 重置修改
3. 查找历史
4. 清理仓库

## 参考资料
1. [Git Documentation](https://git-scm.com/doc)
2. [Pro Git Book](https://git-scm.com/book/en/v2)
3. [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/)
