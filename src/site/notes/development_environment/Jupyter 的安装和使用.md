---
{"dg-publish":true,"dg-permalink":"development_environment/jupyter","permalink":"/development_environment/jupyter/","dgHomeLink":true,"dgPassFrontmatter":false}
---



# Jupyter 的安装和使用


## 安装


```
pip install jupyter

jupyter notebook
```


## 使用


### 修改默认路径

生成配置文件

```
$ jupyter notebook --generate-config
Writing default config to: C:\Users\...\.jupyter\jupyter_notebook_config.py
```

打开上述文件，修改下面内容

```
## The directory to use for notebooks and kernels.
c.NotebookApp.notebook_dir = r'...'
```

