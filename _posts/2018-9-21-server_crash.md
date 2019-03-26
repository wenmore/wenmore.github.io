---
layout: post
title: 记一次服务器瞎操作
key: 20180921
tags: server crash
---

## 起因
    事情是这样的，因为我python3.7的pip在旧的ubuntu14.04中始终出现问题，于是萌生了更新系统的想法，按照这个[教程](https://blog.csdn.net/qq_38391495/article/details/70926791)我开始了~~~

    <!--more-->

    ```bash
    sudo apt update
    sudo apt dist-upgrade
    sudo do-release-upgrade
    ```
    中间越跑越心虚，毕竟这是实验室财产。果然师兄就问我了，你在干嘛！！！我就很慌，我说我在更新服务器系统，紧张地我肚子痛，失去思考能力。师兄让我ctrl c强制停止我......然后然后师兄过来就ctrl啥强制停止了，后来知道，服务器更新中途强制停止服务器要崩溃，果然我们服务器后面就14和16傻傻分不清，我说要不reboot吧，师兄说，你别乱搞，可是我等他们回去后还是reboot了......

    于是搜ubuntu14更新到16 ctrl c怎么恢复，搜到[这样的](https://askubuntu.com/questions/649364/i-hit-control-c-in-a-do-release-upgrade-subprocess-how-do-i-recover)：

    ```bash
    apt-get install --fix-broken
    apt-get update
    apt-get dist-upgrade
    ```
    [这样的](https://askubuntu.com/questions/146308/hit-ctrlc-during-do-release-upgrade-did-i-break-it)
    
    ```bash
    sudo rm /var/lib/dpkg/lock && sudo dpkg --configure -a
    ```

    找到[这样的](https://www.quora.com/Iwas-upgrading-from-Ubuntu-17-04-to-17-10-my-battery-ran-out-just-as-the-downloading-part-finished-how-do-I-continue)it's pretty safe心里是灰常开心的，
    然后悲剧的是发现自己的apt和dpkg根本都用不了。

    首先解决libstdc++.so.6的问题，参考这篇[博客](https://blog.csdn.net/xunianchong/article/details/50434836)，下载自己服务器对应的版本。
    
    ```bash
    uname -a
    lsb_release -a
    cat /proc/version
    ```

    下载服务器系统对应的[版本](https://packages.ubuntu.com/xenial/libstdc++6)，:

    ```bash
    ar -x libstdc++6_5.4.0-6ubuntu1~16.04.10_amd64.deb && tar xvf data.tar.gz
    ```
    会出现一个层次分明的usr文件夹，把这些东西copy到系统相应目录下，拯救了dpkg貌似，于是到[gcc](https://packages.ubuntu.com/xenial/amd64/gcc-5-base/download)
    
    ```bash
    wget http://security.ubuntu.com/ubuntu/pool/main/g/gcc-5/gcc-5-base_5.4.0-6ubuntu1~16.04.10_amd64.deb
    sudo dpkg -i gcc-5-base_5.4.0-6ubuntu1_16.04.10_amd64.deb
    ```
    一点错没报的就乖乖安装好了，宝宝惊呆了。

    这样又发现我们服务器连不了网，因为明明apt, dpkg已能用，[于是]()

    ```bash
    vi /etc/resolv.conf  #nameserver 1.1.1.1
    sudo service resolvconf restart
    ```
    这样进行上述任意apt, dpkg操作都没问题啦，然后就胡乱着按照网上教程运行apt, dpkg相关命令了，该remove的就remove，clean, fix等等操作......

    然后就根据自己想安装什么软件根据该软件依赖什么包下载相应的包，以我python3.7为例，首先配置环境，参考[这个](https://serverfault.com/questions/918335/best-way-to-run-python-3-7-on-ubuntu-16-04-which-comes-with-python-3-5)：

    ```bash
    # Install requirements
    apt-get install -y build-essential
    apt-get install -y checkinstall
    apt-get install -y libreadline-gplv2-dev
    apt-get install -y libncursesw5-dev
    apt-get install -y libssl-dev
    apt-get install -y libsqlite3-dev
    apt-get install -y tk-dev
    apt-get install -y libgdbm-dev
    apt-get install -y libc6-dev
    apt-get install -y libbz2-dev
    apt-get install -y zlib1g-dev
    apt-get install -y openssl
    apt-get install -y libffi-dev
    apt-get install -y python3-dev
    apt-get install -y python3-setuptools

    tar xvf Python-3.7.0.tar.xz
    cd /tmp/Python37/Python-3.7.0
    ./configure --prefix=/home/username/env
    make && make install
    ```
    最后配置pip源，向python学习群里请教知道的。

    ```bash
    mkdir .pip
    vi pip.conf
    ### pip.conf内写入内容
    [global]
    timeout = 120
    index-url = http://pypi.douban.com/simple 
    [install] 
    trusted-host = pypi.douban.com
    ```

    原来系统用不了的老是出错的如下信息：

    ```bash
    pip is configured with locations that require TLS/SSL, however the ssl module in Python is not available.
    Collecting <package>
    Could not fetch URL https://pypi.python.org/simple/<package>/: There was a problem confirming the ssl certificate: Can't connect to HTTPS URL because the SSL module is not available. - skipping
    Could not find a version that satisfies the requirement <package> (from versions: )
    No matching distribution found for <package>
    ```
    最后是这样解决的
    安装一个低版本的openssl-1.0.2h[链接](https://zhuanlan.zhihu.com/p/35640102)

    ```bash
    ./config --prefix=/usr/local --openssldir=/usr/local/openssl  ## 确实直接config的话版本还是原来版本
    make
    sudo make install
    ```

    成功import ssl, 自然就成功安装上了jupyter，嘿嘿。


    然后就先这样吧！！！






