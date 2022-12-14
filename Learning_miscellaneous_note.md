# <center>学习杂记
---
@author iVan
@date 2022-08-24 14:24:33 +0800
## git通过token的方式进行push
源地址:[csdn](https://blog.csdn.net/m0_37844072/article/details/122715958)
https://blog.csdn.net/m0_37844072/article/details/122715958
- 问题描述：git push的时候发现不能push,有如下报错
- >![](./assets/Snipaste_2022-08-24_12-33-22.png)

- 方案:
    - 1.生成token
    - ![](assets/20191122170943600.png)
    - 2.使用token，把生成的token当作密码，用户名是token的名字
    - ![](assets/5505a44f099b49568d25e3b254fbafca.png)

设置完成后，$ git remote -v 可以确认是否已经替换【效果如下】：
![](assets/token-example1.png)

---

## gitignore相关
### 1.当前我使用的gitignore配置如下：
```ignore
# java开发通用模版 ---iVanz---20220824
# 来自 https://blog.csdn.net/duguxueao/article/details/120334763 以及 https://github.com/github/gitignore/blob/main/Java.gitignore

# Compiled class file
*.class

# Log file
*.log

# BlueJ files
*.ctxt

# Mobile Tools for Java (J2ME)
.mtj.tmp/

# Package Files #
*.jar
*.war
*.nar
*.ear
*.zip
*.tar.gz
*.rar

# virtual machine crash logs, see http://www.java.com/en/download/help/error_hotspot.xml
hs_err_pid*
replay_pid*

# ============================

# system ignore
.DS_Store
node_modules/

##uniapp
unpackage/

# Editor directories and files
.idea/
.vscode/
*.suo
*.ntvs*
*.njsproj
*.sln</code></pre> 

# =======================
# python的ignore策略
# 来自：https://github.com/github/gitignore/blob/main/Java.gitignore

# Byte-compiled / optimized / DLL files
__pycache__/
*.py[cod]
*$py.class

# C extensions
*.so

# Distribution / packaging
.Python
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
wheels/
share/python-wheels/
*.egg-info/
.installed.cfg
*.egg
MANIFEST

# PyInstaller
#  Usually these files are written by a python script from a template
#  before PyInstaller builds the exe, so as to inject date/other infos into it.
*.manifest
*.spec

# Installer logs
pip-log.txt
pip-delete-this-directory.txt

# Unit test / coverage reports
htmlcov/
.tox/
.nox/
.coverage
.coverage.*
.cache
nosetests.xml
coverage.xml
*.cover
*.py,cover
.hypothesis/
.pytest_cache/
cover/

# Translations
*.mo
*.pot

# Django stuff:
*.log
local_settings.py
db.sqlite3
db.sqlite3-journal

# Flask stuff:
instance/
.webassets-cache

# Scrapy stuff:
.scrapy

# Sphinx documentation
docs/_build/

# PyBuilder
.pybuilder/
target/

# Jupyter Notebook
.ipynb_checkpoints

# IPython
profile_default/
ipython_config.py

# pyenv
#   For a library or package, you might want to ignore these files since the code is
#   intended to run in multiple environments; otherwise, check them in:
# .python-version

# pipenv
#   According to pypa/pipenv#598, it is recommended to include Pipfile.lock in version control.
#   However, in case of collaboration, if having platform-specific dependencies or dependencies
#   having no cross-platform support, pipenv may install dependencies that don't work, or not
#   install all needed dependencies.
#Pipfile.lock

# poetry
#   Similar to Pipfile.lock, it is generally recommended to include poetry.lock in version control.
#   This is especially recommended for binary packages to ensure reproducibility, and is more
#   commonly ignored for libraries.
#   https://python-poetry.org/docs/basic-usage/#commit-your-poetrylock-file-to-version-control
#poetry.lock

# pdm
#   Similar to Pipfile.lock, it is generally recommended to include pdm.lock in version control.
#pdm.lock
#   pdm stores project-wide configurations in .pdm.toml, but it is recommended to not include it
#   in version control.
#   https://pdm.fming.dev/#use-with-ide
.pdm.toml

# PEP 582; used by e.g. github.com/David-OConnor/pyflow and github.com/pdm-project/pdm
__pypackages__/

# Celery stuff
celerybeat-schedule
celerybeat.pid

# SageMath parsed files
*.sage.py

# Environments
.env
.venv
env/
venv/
ENV/
env.bak/
venv.bak/

# Spyder project settings
.spyderproject
.spyproject

# Rope project settings
.ropeproject

# mkdocs documentation
/site

# mypy
.mypy_cache/
.dmypy.json
dmypy.json

# Pyre type checker
.pyre/

# pytype static type analyzer
.pytype/

# Cython debug symbols
cython_debug/

# PyCharm
#  JetBrains specific template is maintained in a separate JetBrains.gitignore that can
#  be found at https://github.com/github/gitignore/blob/main/Global/JetBrains.gitignore
#  and can be added to the global gitignore or merged into this file.  For a more nuclear
#  option (not recommended) you can uncomment the following to ignore the entire idea folder.
#.idea/
```
## 2.如果已经push到remote，如何使远程仓库更新.gitignore配置?
- gitignore只能忽略那些原来没有被track的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。所以一定要养成在项目开始就创建.gitignore文件的习惯。
解决方法就是先把本地缓存删除(改变成未track状态)，然后再提交，按以下三步执行：
```git
git rm -r --cached .
git add .
git commit -m "msg"
```

## 3.如何定义全局的.gitignore文件?
- 除了可以在项目中定义.gitignore文件外，还可以设置全局的.gitignore文件来管理所有Git项目的行为。
这种方式在不同的项目开发者之间是不共享的，是属于项目之上Git应用级别的行为。
可以在任意目录下创建相应的.gitignore文件，然后再使用以下命令配置Git
```gitignore
git config --global core.excludesfile ~/.gitignore
```
---

## 4.vscode扩展:Insert Date String 使用
- 可以输入一个时间 信息
- 按 Ctrl+Alt+Shift+ I  
- 在默认参数后面增加时区信息 ZZZZ
- 输出效果: 
>```java
>2022-08-24 14:23:41 +0800
>```
---
