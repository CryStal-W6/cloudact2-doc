# 前言

​	Cloud-Act2提供自动化调度和执行能力，与业务解耦，底层的执行可以对接如SaltStack、SSH之类的通道等。用户无需关心底层通道的实现方式，可直接对接Cloud-Act2来使用其提供的自动化操作的能力。

​	Cloud-Act2通过逻辑机房的概念，统一管理实际分散在各个机房的服务器的中间件工具，可以对接SaltStack服务，具备远程管理服务器，向服务器下发指令或脚本的能力，提供跨机房的文件分发能力。

