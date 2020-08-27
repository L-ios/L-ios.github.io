title: Django Tutorials 第一天
tags:
    -Django
    -python
---


# Django 第一天
## django的安装，以及检测

安装django：

```bash
   $ sudo -H pip install django
```

检测django的版本：

```bash
$ python -m django --version
```

错误的输出
```bash
/usr/bin/python: No module named django
FAIL
```

如果电脑中python2和python3并存，可以采用`python2 -m django --verion`或者`python3 -m django --version`来进行尝试。

## 创建项目
创建django命令是使用`django-admin`，命令如下
```bash
$ django-admin startproject [project_label]
```
例如，我在这里创建一个mysite项目
```bash
 $ django-admin startproject mysite
```

django-amin会帮助我们创建一个mysite目录,mysite目录的目录结构如下

```bash
mysite
├── manage.py
├── mysite
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── templates
```
