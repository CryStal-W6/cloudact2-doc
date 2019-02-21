# 任务执行

##文件下发

act2ctl file send [ip_list] src target [options]

通过act2服务下发文件到远程服务器上，ip_list以英文逗号分割的ip地址列表，为远程服务器地址

 

Options：

-H hostfile    指定要下发执行的远程服务器地址，与ip_list互斥

-t type    下发时指定通道类型，type可以为salt或ssh，默认为salt

-s scriptType    脚本类型，支持bash或bat或python或sls，默认为bash。如果提供了系统类型，在Windows下默认为bat，其他默认为bash

-C command    需要执行的命令，与 -f 互斥，最后与脚本执行是一样的

-a arg    脚本或者命令支持的参数，多个参数需要使用单引号或双引号起来，需要注意bash转义

--nocolor    关闭默认输出结果的高亮输出

-ouput format    输出格式，支持 default或json或yaml，其中默认为default，支持高亮输出，json或yaml输出无高亮

-T timeout    脚本执行的超时时间，默认为300s

-c idc    指定idc名称，通道类型为ssh时必须指定

-o ostype    系统类型，支持windows|linux|aix

-u username    指定执行账户，如果未指定，在系统类型为windows时默认账户Administrator，其他系统默认账户为root

-p password    指定执行账户的密码，通常类型为ssh时必须指定

-P port    指定通常类型为ssh时的连接端口，默认为22

-e encoding    指定执行时编码类型，支持gb18030或utf-8，如果未指定，在系统类型为windows时默认为gb18030，其他系统默认账户为utf-8

-v --verbose    输出调试信息

--async    异步处理，返回作业执行任务id

 

示例：

```bash
./act2ctl file send 192.168.1.1,192.168.1.2 test.txt /root/test.txt
./act2ctl file send -H hostfile test.txt /root/test.txt
```



##命令、脚本执行

act2ctl run [options] [ip_list]

通过act2服务下发命令或者脚本到远程服务器上，并进行执行, ip_list以英文逗号分割的ip地址列表，为远程服务器地址，可放在命令行任意位置，一般放在尾部

 

Options:

-H hostfile    指定要下发执行的远程服务器地址，与ip_list互斥

-t type    下发时指定通道类型，type可以为salt或puppet或ssh，目前支持salt或ssh，默认为salt

-f scriptfile    需要执行的脚本文件

-a arg    脚本或者命令支持的参数，多个参数需要使用单引号或双引号起来，需要注意bash转义

-c idc    指定idc名称，通道类型为ssh时必须指定

-u username    指定执行账户，如果未指定，在系统类型为windows时默认账户Administrator，其他系统默认账户为root

-p password    指定执行账户的密码，通常类型为ssh时必须指定

-P port    指定通常类型为ssh时的连接端口，默认为22

-o ostype    系统类型，支持windows|linux|aix

-s scriptType    脚本类型，支持bash或bat或python或perl或sls，默认为bash。如果提供了系统类型，在Windows下默认为bat，其他默认为bash

-e encoding    指定执行时编码类型，支持gb18030或utf-8，如果未指定，salt版本为2018.3.3时，windows系统默认时使用utf-8，在salt版本为2018.3.3之前，windows系统默认使用gb18030，其他系统默认账户为utf-8

-C command    需要执行的命令，与 -f 互斥，最后与脚本执行是一样的

-T timeout    脚本执行的超时时间，默认为300s

--nocolor    关闭默认输出结果的高亮输出

-ouput format    输出格式，支持 default或json或yaml，其中默认为default，支持高亮输出，json或yaml输出无高亮

-v  --verbose    输出调试信息

--async    异步处理，返回作业执行任务id

 

示例：

指定IP地址执行命令（使用默认salt通道）

```bash
./act2ctl run 192.168.1.1 -C 'df -h'
```

指定IP执行脚本并添加参数（使用默认salt通道）

```bash
./act2ctl run 192.168.1.1 -f test.sh -a "hello act2"
```

指定IP执行脚本并添加参数（使用SSH通道）

```bash
./act2ctl run 192.168.1.1 -t ssh -f test.sh -a "hello act2" -o linux -c hangzhou
```

异步任务（使用SSH通道）

 ```bash
./act2ctl run 192.168.1.1 -t ssh -f test.sh -a "hello act2" -o linux -c hangzhou --async
 ```

