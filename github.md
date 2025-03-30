以下是创建 Git 仓库的详细步骤，包含本地仓库创建、远程仓库关联和基础操作流程：

---

### **一、本地创建 Git 仓库**
#### **1. 初始化空仓库**
```bash
# 进入项目目录
cd /path/to/your/project

# 初始化本地仓库
git init
```
终端会显示：`Initialized empty Git repository in /your/path/.git/`

#### **2. 配置基础信息（首次使用需设置）**
```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱@example.com"
```

#### **3. 添加文件到暂存区**
```bash
# 添加所有文件（包括新建和修改）
git add .

# 或添加指定文件
git add index.html style.css
```

#### **4. 提交到本地仓库**
```bash
git commit -m "初始提交：创建项目基础结构"
```

---

### **二、关联远程仓库（以 GitHub 为例）**
#### **1. 创建远程仓库**
1. 登录 GitHub → 点击右上角 ➕ → New repository
2. 填写仓库名（如 `my-blog`）
3. 选择公开（Public）或私有（Private）
4. **不要勾选**初始化 README/.gitignore（本地已有项目）

#### **2. 关联远程地址**
```bash
# 复制仓库SSH地址（推荐）或HTTPS地址
git remote add origin git@github.com:你的用户名/my-blog.git
```

#### **3. 验证远程关联**
```bash
git remote -v
```
正确显示：
```
origin  git@github.com:你的用户名/my-blog.git (fetch)
origin  git@github.com:你的用户名/my-blog.git (push)
```

#### **4. 首次推送代码**
```bash
git push -u origin master  # 如果分支名为 main 则替换为 main
```
出现 `Writing objects: 100%` 表示推送成功

---

### **三、日常开发工作流**
#### **1. 典型操作流程**
```bash
# 拉取最新代码（多人协作时）
git pull origin master

# 开发新功能后...
git add .
git commit -m "实现文章列表页布局"

# 推送到远程
git push origin master
```

#### **2. 分支管理（可选）**
```bash
# 创建新功能分支
git checkout -b feature/article-page

# 合并分支到主分支
git checkout master
git merge feature/article-page
```

---

### **四、常用配置优化**
#### **1. 忽略不需要跟踪的文件**
创建 `.gitignore` 文件：
```text
# 忽略 node_modules
node_modules/

# 忽略 IDE 配置文件
.vscode/
.idea/

# 忽略系统文件
.DS_Store

# 忽略本地环境配置
.env
```

#### **2. 查看仓库状态**
```bash
git status  # 查看修改状态
git log     # 查看提交历史
```

---

### **五、常见问题解决**
#### **1. 推送失败（权限问题）**
```bash
# 检查SSH密钥配置
ssh -T git@github.com  # 应显示 "You've successfully authenticated"

# 或切换为HTTPS方式：
git remote set-url origin https://github.com/你的用户名/my-blog.git
```

#### **2. 提交错分支**
```bash
# 将提交移动到新分支
git branch correct-branch
git reset HEAD~ --hard
git checkout correct-branch
```

---

### **六、可视化工具推荐**
1. **VSCode 内置 Git 工具**：直观查看文件修改状态
2. **GitKraken**：图形化界面操作分支
3. **SourceTree**：免费的可视化 Git 客户端

完成上述操作后，你的项目已具备完整的版本控制能力。建议每天开发前先执行 `git pull`，完成功能后及时 `commit + push`。