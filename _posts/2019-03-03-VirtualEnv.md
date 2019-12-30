---
title: Virtualenv - Isolated Environments for Python Programming
tags: Python, Mac
---

As a developer that deals with Python a lot, packages end up becoming a big issue. After installing packages for one project, those dependencies might end up conflicting with your new project. Another case, involves trying to solve a dependency problem, but to solve a dependency you follow some random tutorial online and mess up all of your Python packages. In order to alleviate this problem, Virtualenv was created for isolated Python Programming.
This tutorial uses a Mac to install of the packages.

#### What is Virtualenv?

Virtualenv is a tool that allows developers to create isolated environments for their Python projects. With Virtualenv you can create such environments and install packages without affecting other projects or your native environment on your computer. You can simply 'pip' install a package and it will stay in your Virtualenv without also conflicting other Virtualenv's that you already crated.


#### Installing Virtualenv

The description above won't really make sense until you install and try it for yourself. First let's check if you have Python on your computer by opening up your terminal and typing:

```shell
$ python --version
```

If you don't have Python installed I would install Python 3.6 at least by going to the Official Python site. Let's install the pip:

```shell
$ sudo easy_install pip
```

Now we never have to hopefully use easy_install after. Let's download Virtualenv:

```shell
$ pip install virtualenv
```

Then check to see if it is install successfully:

```shell
$ virtualenv --version
```

Just for reference, my current version is:

```shell
16.4.1
```

#### Creating your first isolated environment

Now that you have installed Virtualenv, let's create our first isolated environment.

```shell
# Name the folder what ever you want
$ mkdir projectfolder
$ cd projectfolder

# Change the name to whatever you want, but make it some what short
$ virtualenv env
```

By default, Virtualenv will not include global packages into your isolated environment. This means anything that you have installed on your native system will not be shown in your environment.

Now after that command, you should see a folder named after the environment you created. Now let's activate the environment.

```shell
# This is one way
$ source env/bin/activate

# A lot of other tutorials will just go into the env and activate it.
$ cd env/bin
$ source activate
```

You should get something like this in your terminal:

![](/img/2019-03-03-Virtualenv/terminal_env_name.png)

This shows that you are in the Virtualenv. Let's first see your Python Version:

```shell
$ python --version
```

The python version should be your default python version on your native computer.

Now let's check your dependencies:

```shell
$ pip freeze
```

The result should be nothing. That's because you don't have any packages installed. Let's install flask:

```shell
$ pip install flask
```

Then run pip freeze again:

```shell
$ pip freeze
```

You should get something like this:

```shell
Click==7.0
Flask==1.0.2
itsdangerous==1.1.0
Jinja2==2.10
MarkupSafe==1.1.1
Werkzeug==0.14.1
```

You might be wondering it might be nice to develop in this isolated environment, but then how do I transfer out these dependencies? One way you can do this is by simply exporting you dependencies into a 'requirements.txt'. You can do this with this command:

```shell
$ pip freeze > requirements.txt
```

After this, you should see a new file show up called requirements.txt show up. In a different environment you can install this with:

```shell
$ pip install -r requirements.txt
```

Now let's deactivate your environment:

```shell
$ deactivate
```

You can run this command in any directory without having to go back to the environment folder.

#### Tips

- When developing for a project, a good practice is to have a ".gitignore" that does not upload your Virtualenv to your Github. One that I use all the time is made from this person: https://github.com/github/gitignore/blob/master/Python.gitignore. The common name for a Virtualenv is 'env'. I also name my Virtualenv's this in my Github projects just in case I accidentally forget to put it in.

- If you want to use a specific version of Python when creating a Virtualenv you can use this command:

```shell
$ virtualenv --python=/path/to/python-version env
```


#### Conclusion

Virtualenv is a great way and start to managing your Python Projects. This allows for easier rapid development since you can spin a Virtualenv up in any folder at any time as long as you have it installed.


#### Resources used to make this article:

- Gitignore for Python Projects: https://github.com/github/gitignore/blob/master/Python.gitignore
- Official Site for Virtualenv: https://virtualenv.pypa.io/en/latest/
- Official Documentation for Pip freeze: https://pip.pypa.io/en/stable/reference/pip_freeze/
