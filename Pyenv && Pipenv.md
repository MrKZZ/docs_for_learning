# Pyenv: Simple Python Version Management

 

## Summary :

Pyenv  makes it easily switch between multiple versions of Python. It helps changes the global Python version.

It helps change Python versions on a per-user basis and per-project. It can override the Python version with an environment variable.



## Understanding Path:

when running a python or pip, os searches through a list of dirs to find an executable file with that name. This list of dirs lives in an environment variable callen PATH. Each dir in the list separated by a colon:

```bash
/usr/local/bin:/usr/bin:/bin
```

the searching will start from left to right, so matching executable in a directory at the begging of the list takes precedence over another one at the end.



## Choose the Python Version:

1. The `PYENV_VERSION` environment variable (if specified). You can use the [`pyenv shell`](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md#pyenv-shell) command to set this environment variable in your current shell session.
2. The application-specific `.python-version` file in the current directory (if present). You can modify the current directory's `.python-version` file with the [`pyenv local`](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md#pyenv-local) command.

## Commands:

pyenv install 3.6.8. 

Pyenv uninstall 3.6.8

pyenv global 3.6.8.  设置全局python版本

pyenv local 3.6.8  设置局部python版本（当前目录下）

pyenv shell 3.6.8  设置当前命令行下python版本

pyenv versions 查看当前pyenv中所包含的python版本

# Pipenv: Python Development Workflow for HUman 

pipenv是用来构建虚拟环境的。piping 用来进行保管理。

创建一个虚拟环境：Pipenv —python 3.6.8 

安装项目的全部依赖：pipenv install —dev

显示安装的依赖： pipenv graph

pipenv shell 进入当前目录虚拟环境

exit 推出虚拟环境

pipenv install urllib  安装指定包 —dev 表示安装包指定依赖

pipenv uninstall urllib. 删除指定包

Pipenv update xxx 更新指定包

pipenv —vena 查看虚拟环境目录.