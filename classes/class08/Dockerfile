FROM debian:bookworm

RUN apt update && apt install -y openssh-server gdb vim nano tmux make gcc python3 checksec python3-pip git

RUN pip3 install --user ropper --break-system-packages

RUN mkdir -p /var/run/sshd
RUN mkdir -p /root/.ssh

COPY sshd_config /etc/ssh/sshd_config
COPY files /data/binary-exploit-class

ENV TERM=xterm-256color

RUN echo "PS1='\e[92m\u\e[0m@\e[94m\h\e[0m:\e[35m\w\e[0m# '" >> /root/.bashrc
RUN echo "root:admin" | chpasswd
RUN echo 'PATH=$PATH:/root/.local/bin' >> /root/.bashrc # for the ropper binary

CMD ["/usr/sbin/sshd", "-D"]
