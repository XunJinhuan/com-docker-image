FROM centos:centos7

RUN yum install -y vim && \
    yum install -y net-tools.x86_64 && \
    echo "root:yangpeng" | chpasswd && \
    yum install -y openssh-server && \
    yum install -y openssh-clients && \
    yum clean all && \
    sed -i "s/#Port 22/Port 22/" /etc/ssh/sshd_config && \
    sed -i "s/#ListenAddress 0.0.0.0/ListenAddress 0.0.0.0/" /etc/ssh/sshd_config && \
    sed -i "s/#ListenAddress ::/ListenAddress ::/" /etc/ssh/sshd_config && \
    sed -i "s/#PermitRootLogin yes/PermitRootLogin yes/" /etc/ssh/sshd_config && \
    sed -i "s/#PasswordAuthentication yes/PasswordAuthentication yes/" /etc/ssh/sshd_config && \
    sed -i "s/#PubkeyAuthentication yes/PubkeyAuthentication yes/" /etc/ssh/sshd_config && \
    ssh-keygen -q -t rsa -b 2048 -f /etc/ssh/ssh_host_rsa_key -N "" && \
    ssh-keygen -q -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key -N "" && \
    ssh-keygen -t dsa -f /etc/ssh/ssh_host_ed25519_key -N "" && \
    # /sbin/sshd && \
    ssh-keygen -t rsa -P '' -f ~/.ssh/id_rsa && \
    cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys && \
    chmod 0600 ~/.ssh/authorized_keys