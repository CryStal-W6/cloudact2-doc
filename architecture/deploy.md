# 部署架构

​	Cloud-Act2 Master部署在最上层，统一管理所有的Cloud-Act2 Proxy节点，将从Cloud-Act2 Proxy接收到的信息保存到数据库中，需要保持与Cloud-Act2 Proxy和数据库的网络畅通。

​	Cloud-Act2 Proxy部署在各idc机房，同时需要部署Salt-Master，SaltStack版本为2018.3.3，通过Salt-Master接收被管理服务器上Salt-Minion收集到的信息，然后将信息传递给Cloud-Act2 Proxy，再将其上报给Cloud-Act2 Master。

​	被管理服务器需要安装Salt-Minion，SaltStack版本为2018.3.3，用于信息收集上报，同时作为Cloud-Act2的默认执行通道。

