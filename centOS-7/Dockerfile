FROM centos:7

RUN sed -i 's|^mirrorlist=|#mirrorlist=|g' /etc/yum.repos.d/CentOS-Base.repo && \
    sed -i 's|^#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-Base.repo

RUN yum update -y && \
    yum install -y openssh-server openssh-clients sudo && \
    mkdir /var/run/sshd && \
    echo 'root:rootpassword' | chpasswd && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's@^#Subsystem\tsftp@Subsystem\tsftp /usr/libexec/openssh/sftp-server@g' /etc/ssh/sshd_config && \
    ssh-keygen -A && \
    yum clean all

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]

