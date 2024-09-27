# Usa la imagen base de Ubuntu 18.04
FROM ubuntu:18.04

# Actualiza los paquetes e instala OpenSSH
RUN apt-get update && \
    apt-get install -y openssh-server sudo && \
    mkdir /var/run/sshd && \
    echo 'root:rootpassword' | chpasswd && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's@^#Subsystem\tsftp@Subsystem\tsftp /usr/lib/openssh/sftp-server@g' /etc/ssh/sshd_config && \
    ssh-keygen -A && \
    apt-get clean

# Exponer el puerto SSH
EXPOSE 22

# Comando para iniciar el servicio SSH
CMD ["/usr/sbin/sshd", "-D"]
