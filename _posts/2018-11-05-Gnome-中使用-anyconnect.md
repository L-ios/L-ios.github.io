---
layout: post
title: Gnome 中使用 anyconnect
subtitle: 在 Gnome NetworkManager 中使用 anyconnect
tags: [Linux, Gnome, Vpn, anyconnect]
comments: true
date: 2018-11-05 22:17:08
---

Linux 有对应的Cisco Anyconnect官方的客户端，不好找，而且还在连接成功后自动的断掉，为了方便使用，我们使用gnome自带的NetworkManger进行管理
1. 安装相应的软件包 `network-manager-openconnect` 和 `network-manager-openconnect-gnome`
2. 使用systemctl重载 `NetworkManager.service`
```shell
sudo systemctl reload NetworkManager.service
```
3. 找到设置=>网络=>新建vpn，如下图选择
![choose a vpn connection type](/assets/img/post/2018/11/06/anyconnect_1.png)

图.1 此处选择openconnect
4. 填写vpn信息
![add vpn base info](/assets/img/post/2018/11/06/anyconnect_2.png)

图.2首先选择vpn的协议类型为 anyconnect，在 Gateway 填入 vpn 服务器地址
**注意:** 使用密码登录,这里就好了,直接保存,并在设置中开启vpn,这里如果什么都没有现在,可能是 `gnome-keyring-daemon` 没有启动
5. 适当修改dns,关闭下图中Automatic
![change vpn dns](/assets/img/post/2018/11/06/anyconnect_3.png)
图.3
6. 基于证书的认证方式
    a. 证书和私钥分离
    ```shell
    openssl pkcs12 -in zhengshu.pfx -nocerts -nodes -out user.key
    openssl pkcs12 -in zhengshu.pfx -clcerts -nokeys -out user.crt
    ```
    b. 在图.2 中的 `User Certificate` 中填写生成的 `user.crt`
    c. 在图.2 中的 `Private Key` 中填写生成的 `user.key`
