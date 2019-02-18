# 整体架构

​	Cloud-Act2产品技术组件包括Cloud-Act2 Master和Cloud-Act2 Proxy，Cloud-Act2 Proxy分布于各机房，Cloud-Act2 Master通过管理各机房的Cloud-Act2 Proxy来实现对各机房服务器的管理。其上可对接用户自己的统一管理平台，屏蔽底层通道。

​	

​	Cloud-Act2 Master：负责作业的调度分发，包括黑名单及ACL访问控制功能。收集Cloud-Act2 Proxy采集的设备信息、执行结果信息，并将其保存到数据库中。

​	Cloud-Act2 Proxy：接收Cloud-Act2 Master下发的指令，然后将指令转发给底层执行通道（SaltStack、Puppet、SSH）执行。采集被管理的服务器信息和执行结果信息，并上报给Cloud-Act2 Master。