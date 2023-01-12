# ELS
ELS为HPC使用者和HPC业务平台开发者提供了一套统一的使用标准，HPC集群的使用者仅需根据ELS提供的使用标准即可在ELS所支持的所有作业调度系统上运行你的作业，理论上可以适配（slurm、pbs、lsf等）任何HPC作业调度系统。  

### Server端安装使用
``` shell
git clone https://github.com/lizazacn/ELS.git # 克隆该仓库
cd ELS # 切换到仓库目录目录
chown 0600 ./etc/conf.json # 修改配置文件权限
./ELSServer # 直接运行二进制文件
```
## 目前工作进度
开发完成API接口作业提交和RPC接口作业提交

## ELS功能
| 命令       | 接口地址      | 功能          | 备注                                                           |
|----------|-----------|-------------|--------------------------------------------------------------|
| einfo    | /einfo    | 查看可用队列信息    ||
| erun     | /erun     | 交互式作业提交     | 该命令API接口提供两种访问方式，无交互时请求类型为POST，有交互时请求类型为websocket长连接         |
| ebatch   | /ebatch   | 批处理作业提交     | 如果以输入流的方式传递批处理文件，首行必须为'#!/bin/bash'、'#!/bin/sh'、'#!/bin/csh'之一 |
| ejobs    | /ejobs    | 查看当前正在运行的作业 ||
| ehis     | /ehis     | 查看历史作业      ||
| econtrol | /econtrol | 管理作业调度系统    | 以slurm为例，此命令可以用来调整slurm的分区等配置信息                              |
| ekill    | /ekill    | 结束作业        ||
| emgr     | /emgr     | 管理els系统     ||
| login    | /login    | 登录调度系统      | 该接口主要提供API使用                                                 |

## 后续计划
1、在不同调度系统的登录节点安装该命令实现操作统一  
2、针对已有的Server端升级实现自动选择的调度系统和计算集群进行计算  
3、针对当前Server端设计客户端以屏蔽底层调度系统的差异  
4、集成一种方案实现软件一次安装多集群运行（考虑容器技术）

## 如有需要请联系：lizaza@lizaza.cn
