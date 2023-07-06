# Milvus-install-ubuntu20.4
此文主要讲述如何在ubuntu20.4里安装Milvus

# 安装Docker
## 安装
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

会输出类似的内容
```
docker.service - Docker Application Container Engine
     Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2020-05-21 14:47:34 UTC; 42s ago
```
## 设定非root用户身份执行Docker
输入下述代码，其中`$USER`替换成当前用户名：

`sudo usermod -aG docker $USER`

# 安装Milvus
此处参考[官网文档](https://milvus.io/docs/install_standalone-docker.md)，详细可看参考文章，这里只作简要安装说明。

依次运行下列代码：
1. `wget https://github.com/milvus-io/milvus/releases/download/v2.2.11/milvus-standalone-docker-compose.yml -O docker-compose.yml`
2. `sudo docker-compose up -d`

等安装完成后，即可看到
```
Creating milvus-etcd  ... done
Creating milvus-minio ... done
Creating milvus-standalone ... done
```

你也可以查看容器状态

`docker-compose ps`

如果成功的话，会显示下列信息：
```
      Name                     Command                  State                            Ports
--------------------------------------------------------------------------------------------------------------------
milvus-etcd         etcd -advertise-client-url ...   Up             2379/tcp, 2380/tcp
milvus-minio        /usr/bin/docker-entrypoint ...   Up (healthy)   9000/tcp
milvus-standalone   /tini -- milvus run standalone   Up             0.0.0.0:19530->19530/tcp, 0.0.0.0:9091->9091/tcp

```
