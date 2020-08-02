---
toc: true
layout: post
description: 连接服务器上的 jupyter 进行远程开发
categories: [jupyter]
title: 远程连接 Jupyter lab/notebook
comments: true
---

### **直接连接**

首先运行远程的 Jupyter Lab 或者 Jupyter Notebook

```bash
jupyter-lab --no-browser --port=port_num
	To access the notebook, open this file in a browser:
		file:///xxxxxxxxxxxxxxxxxxxxx.html
	Or copy and paste one of these URLs:
		http://localhost:port_num/?token=jupyterlab_token
```
此时记下 jupyter 的地址

然后 ssh 端口转发。目标端口要和 jupyter 的端口一致

```bash
ssh -f usr@remote_server -N -L port_num:localhost:port_num
```

`-L 端口转发 本地网卡地址(可省):本地端口:目标地址:目标端口`

`-N 不执行远程命令. 用于转发端口`

`-f 要求 在执行命令前退至后台`

在本地浏览器中打开之前记下的 jupyter 地址，即可使用 JupyterLab。

### **跳转连接**
（未测试）
有时需要先登录某个中转服务器，才能登录到你想要的服务器。这时候与前者类似，只是需要多建立一层ssh连接。首先建立与中转服务器的连接

```bash
ssh -f usr@remote_serverA -N -L port_num:localhost:port_num
```

然后登录中转服务器，建立与目标服务器的连接

```bash
ssh -X usr@remote_serverA
(remote_serverA) $ ssh -f usr@remote_serverB -N -L port_num:localhost:port_num
```

登录目标服务器，运行JupyterLab

```bash
(remote_serverA) $ ssh -X usr@remote_serverB
(remote_serverB) $ jupyter-lab --no-browser --port=port_num
```

最后在本地浏览器打开网址。