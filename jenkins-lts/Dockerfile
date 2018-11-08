# 为了在Jenkins容器中使用宿主机的docker，自定义Docekerfile
FROM jenkins/jenkins:lts
MAINTAINER xmc

USER root
# 替换为阿里云的jessie
RUN echo '' > /etc/apt/sources.list.d/jessie-backports.list \
  && echo "deb http://mirrors.aliyun.com/debian jessie main contrib non-free" > /etc/apt/sources.list \
  && echo "deb http://mirrors.aliyun.com/debian jessie-updates main contrib non-free" >> /etc/apt/sources.list \
  && echo "deb http://mirrors.aliyun.com/debian-security jessie/updates main contrib non-free" >> /etc/apt/sources.list

# 安装 docker 依赖库
RUN apt update && apt install -y libltdl7
# 添加jenkins到docker权限组 994 是docker用户组权限，可能需要根据宿主机docker用户组ID一致（未验证）
RUN groupadd -g 994 docker &&  usermod -a -G docker jenkins

# 切换回 jenkins用户
USER jenkins
