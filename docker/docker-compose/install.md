使用docker-compose方式快速部署及验证
1.首先准备dockerk及docker-compose环境，如果有，跳过该步骤执行后续步骤
因为使用甲骨文韩国主机，连接外网比较方便，直接使用yum安装即可
```yaml

yum update
yum install docker-ce 
```

```text
[root@arm-01 ~]# yum install docker-ce 
Last metadata expiration check: 4:16:19 ago on Sun 23 Apr 2023 01:14:30 AM UTC.
Dependencies resolved.
====================================================================================================================================================================================================================================
 Package                                                         Architecture                                  Version                                                 Repository                                              Size
====================================================================================================================================================================================================================================
Installing:
 docker-ce                                                       aarch64                                       3:23.0.4-1.el8                                          docker-ce-stable                                        14 M
Installing dependencies:
 docker-ce-cli                                                   aarch64                                       1:23.0.4-1.el8                                          docker-ce-stable                                       6.2 M
 docker-ce-rootless-extras                                       aarch64                                       23.0.4-1.el8                                            docker-ce-stable                                       4.2 M
Installing weak dependencies:
 docker-buildx-plugin                                            aarch64                                       0.10.4-1.el8                                            docker-ce-stable                                        10 M
 docker-compose-plugin                                           aarch64                                       2.17.2-1.el8                                            docker-ce-stable                                        10 M

Transaction Summary
====================================================================================================================================================================================================================================
Install  5 Packages

Total download size: 45 M
Installed size: 210 M
Is this ok [y/N]: y
Downloading Packages:
(1/5): docker-ce-cli-23.0.4-1.el8.aarch64.rpm                                                                                                                                                        38 MB/s | 6.2 MB     00:00    
(2/5): docker-ce-rootless-extras-23.0.4-1.el8.aarch64.rpm                                                                                                                                            33 MB/s | 4.2 MB     00:00    
(3/5): docker-ce-23.0.4-1.el8.aarch64.rpm                                                                                                                                                            22 MB/s |  14 MB     00:00    
(4/5): docker-buildx-plugin-0.10.4-1.el8.aarch64.rpm                                                                                                                                                4.8 MB/s |  10 MB     00:02    
(5/5): docker-compose-plugin-2.17.2-1.el8.aarch64.rpm                                                                                                                                               4.6 MB/s |  10 MB     00:02    
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                                                                18 MB/s |  45 MB     00:02  
...
Installed:
  docker-buildx-plugin-0.10.4-1.el8.aarch64      docker-ce-3:23.0.4-1.el8.aarch64      docker-ce-cli-1:23.0.4-1.el8.aarch64      docker-ce-rootless-extras-23.0.4-1.el8.aarch64      docker-compose-plugin-2.17.2-1.el8.aarch64     

Complete!
...

```
修改docker 目录位置,可以跳过该步骤
```sh
mkdir /etc/docker -p
cat >> /etc/docker/daemon.json  <<EOF
{
"data-root": "/data/docker"
}
EOF
```

查看docker服务及docker-compose是否正常运行
```sh
docker -v
docker-compose version
```

```text
[root@arm-01 data]# docker -v
Docker version 23.0.4, build f480fb1
[root@arm-01 data]# docker-compose version
Docker Compose version v2.17.2
```

![](/img/Snipaste_2023-04-23_13-57-04.jpg)

安装git
![](/img/Snipaste_2023-04-24_09-52-05.jpg)