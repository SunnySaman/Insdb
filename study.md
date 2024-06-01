## git 
```shell
$ git config --global user.name "Grey Li"  # 替换成你的名字
$ git config --global user.email "withlihui@gmail.com"  # 替换成你的邮箱地址

$ git init
Initialized empty Git repository in ~/watchlist/.git/

$ nano .gitignore
# 内容：
*.pyc
*~
__pycache__
.DS_Store
# 使用 Control + O 和 Enter 键保存，然后按下 Control + X 键退出
```

## 将程序托管到 GitHub
### 设置 SSH 密钥¶
一般情况下，当推送本地改动到远程仓库时，需要输入用户名和密码。因为传输通常是通过 SSH 加密，所以可以通过设置 SSH 密钥来省去验证账号的步骤。
1. 首先使用下面的命令检查是否已经创建了 SSH 密钥：

`cat ~/.ssh/id_rsa.pub`

2. 如果显示“No such file or directory”，就使用下面的命令生成 SSH 密钥对，否则复制输出的值备用：

`ssh-keygen`

3. 一路按下 Enter 采用默认值，最后会在用户根目录创建一个 `.ssh` 文件夹，其中包含两个文件，`id_rsa` 和 `id_rsa.pub`，前者是私钥，不能泄露出去，后者是公钥，用于认证身份，就是我们要保存到 GitHub 上的密钥值。

4. 选中并复制`cat ~/.ssh/id_rsa.pub`输出的内容，访问 GitHub 的 SSH 设置页面(https://github.com/settings/keys)（导航栏头像 - Settings - SSH and GPG keys），点击 New SSH key 按钮，将复制的内容粘贴到 Key 输入框里，再填一个标题，比如“My PC”，最后点击“Add SSH key”按钮保存。


### 创建远程仓库

1. 访问新建仓库页面（导航栏“+” - New repository），在“Repository name”处填写仓库名称，这里填“Insdb”即可，接着选择仓库类型（公开或私有）等选项，最后点击“Create repository”按钮创建仓库。

2. 指定本地仓库的远程仓库地址：

`git remote add origin https://github.com/SunnySaman/Insdb.git`

3. 这会为本地仓库关联一个名为“origin”的远程仓库

`git clone https://github.com/SunnySaman/Insdb.git`

### 创建虚拟环境
虚拟环境是独立于 Python 全局环境的 Python 解释器环境，使用它的好处如下：

保持全局环境的干净
为同一个库在不同环境下指定不同的版本
方便记录和管理某个项目相关的依赖
我们将使用 `Python 3 内置的 venv 模块`创建虚拟环境，使用下面的命令即可为当前项目创建一个虚拟环境：


`$ python -m venv insdbenv  # Windows`
或：
`$ python3 -m venv env  # Linux 和 macOS`
提示 上述命令的最后一个参数是虚拟环境名称，你可以自由定义，比如 venv、env、.venv，或是“项目名-venv”，这里使用了 env。

这会在当前目录创建一个包含 Python 解释器环境的虚拟环境文件夹，名称为 env。

### 激活虚拟环境
1. 创建虚拟环境后，我们可以使用下面的命令来激活虚拟环境（通过执行/“source”环境内的激活脚本实现）：

`.\insdbenv\Scripts\activate # windows`
或：
`env/bin/activate  # Linux 或 macOS`
这时命令提示符前会显示虚拟环境的名称，表示已经激活成功：
`(insdbenv) $`
2. 在激活虚拟环境后，无论操作系统和 Python 版本，都可以统一使用 python 和 pip 命令来调用当前虚拟环境内的 Python 和 pip 程序/二进制文件。此时执行 python 或 pip 命令指向的程序和激活脚本在同一个目录下，在 Windows 下所在目录为 env\Scripts\，Linux 和 macOS 下所在目录为 env/bin/。

3. 最后，执行 deactivate 即可退出虚拟环境：
`(insdbenv) $ deactivate`
注意 除了 Git 相关命令外，除非特别说明，后续的所有命令均需要在激活虚拟环境后执行。
提示 建议为 pip 更新 PyPI 源，改为使用国内的 PyPI 镜像源以提高下载速度，具体见这篇文章(https://zhuanlan.zhihu.com/p/57872888)。


## 安装 Flask
激活虚拟环境后，使用下面的命令来安装 Flask：
`(insdbenv) $ pip install flask`
or 指定版本
`(insdbenv) $ pip install flask==2.1.3`





