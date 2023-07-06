# Milvus-install-ubuntu20.4
此文主要讲述如何在ubuntu20.4里安装Milvus

# 安装Docker
此处安装[参考文章](https://zhuanlan.zhihu.com/p/143156163)，详细可看参考文章，这里只作简要安装说明(安装最新版)。

依次运行下列代码：
1. `sudo apt update`
2. `sudo apt install apt-transport-https ca-certificates curl gnupg-agent software-properties-common`
3. `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
4. `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"`
5. `sudo apt update`
6. `sudo apt install docker-ce docker-ce-cli containerd.io`

至此，你已成功安装Docker，你可以输入下列命令来验证

`sudo systemctl status docker`

会输出类似的类容
```
docker.service - Docker Application Container Engine
     Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2020-05-21 14:47:34 UTC; 42s ago
```
