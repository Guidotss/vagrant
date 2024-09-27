FROM ubuntu:18.04

RUN apt-get update && \
    apt-get install -y openssh-server sudo && \
    mkdir /var/run/sshd && \
    echo 'root:rootpassword' | chpasswd && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's@^#Subsystem\tsftp@Subsystem\tsftp /usr/lib/openssh/sftp-server@g' /etc/ssh/sshd_config && \
    ssh-keygen -A && \
    apt-get clean

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
