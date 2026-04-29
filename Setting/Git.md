Git Bash Here

### 基础设置

#### 查看当前目录
pwd
#### 切换目录
cd /path/to/directory
cd ..          # 返回上一级
cd ~           # 回到用户主目录
#### 列出文件和文件夹
ls             # 简单列表!
ls -la         # 详细列表（包括隐藏文件）
#### 设置全局用户名和邮箱
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
#### 查看配置
git config --list
git config user.name  # 查看特定配置

### 新建仓库
#### 创建新仓库
git init
#### 克隆已有仓库
git clone https://github.com/username/repository.git
git clone https://github.com/username/repository.git my-folder  # 指定文件夹名

### 基本流程
1. 先远程同步： 
		git pull
2. 进行代码修改
3. 添加文件到暂存区：
		git add filename.txt          # 添加特定文件
		git add .                     # 添加所有文件
		git add .js                  # 添加所有js文件
		git add folder/               # 添加整个文件夹
4. 提交更改： 
		git commit -m "提交描述信息"
		git commit -am "提交所有已跟踪文件的更改"  # 跳过git add步骤
5. 检查分支
		git branch
		修改分支名： git branch -M main
6. 推送到云端
	1. git push origin main
	2. git push origin master # 默认分支为 master
	3. 第一次push需要绑定 git push -u origin main；以后就可以直接 git push

### 其他

#### 查看当前状态
git status
#### 查看本地commit
git log
git log --oneline
#### 拉取远程更新，但是不合并
git fetch origin 


