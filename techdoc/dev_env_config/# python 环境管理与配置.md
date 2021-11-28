# python 环境管理与配置

## pyenv 

```
brew install pyenv
brew uninstall pyenv
```


查询可安装的 python 版本

```
pyenv install --list
```

安装指定版本

```
pyenv install 3.8.5
```

查询当前所有已安装版本

```
pyenv versions
```

---

配置当前系统所使用的 python 版本

```
pyenv global <xxxxx>
pyenv shell <xxxxx>
eval "$shell"
```


查看当前全局所使用的 python 版本

```
pyenv global 
```



**项目虚拟环境管理**

注意 poetry 的安装是基于现有 python 的，因此 pyenv 可以先指定 shell 的 python 版本再安装。


```
poetry install
source .venv/bin/activate
```


pycahrm 插件：

```
EnvFile
```


**poetry**


```
poetry init # 初始化已经存在的项目
poetry add pendulum # 添加模块（或者修改 `pyproject.toml`文件）
```
