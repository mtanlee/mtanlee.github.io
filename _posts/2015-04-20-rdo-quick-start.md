#ROD QUICK START
###1.更新packages
```bash
sudo yum update -y
```
###2.安装RDO源
```bash
sudo yum install -y https://rdo.fedorapeople.org/rdo-release.rpm
```
##两种安装模式
###3.1.安装all-in-one
```bash
sudo packstack --allinone
```
###3.2.根据需求修改配置文件
```bash
sudo packstack --gen-answer-file /root/answers.txt
sudo vim answers.txt ;可将单节点改为多节点
[general]
...
CONFIG_CONTROLLER_HOST=$ip_controller;控制节点ip地址
CONFIG_COMPUTE_HOSTS=$ip_compute     ;计算节点ip地址
CONFIG_NETWORK_HOSTS=$ip_network     ;网络节点ip地址
...

sudo packstack --answer-file /root/answers.txt
```
