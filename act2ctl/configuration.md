# 配置

act2ctl config add [options] <cluster_server>

配置act2的服务器访问地址。cluster_server是act2的集群对外暴露的服务地址，相关配置信息会存储在~/.act2.yaml文件中

 

Options：

-c    设置cluster地址

-a,--auth    设置auth的类型，默认是basic

-u.--username    auth下的用户名

-p,--password    密码

-i,--waitInterval    查询结果的等待时间

-s,--salt   salt的版本信息设置，通常默认即可

 

config show 

显示act2配置文件内容



示例：

```bash
./act2ctl config add -c <http://192.168.1.1:6868>
./act2ctl config show
```

 