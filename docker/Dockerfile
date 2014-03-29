FROM ubuntu
 MAINTAINER Xiuyu Li nickleefly@gmail.com
 
 # Update apt sources list to fetch mongodb and a few key packages
 RUN echo "deb http://archive.ubuntu.com/ubuntu precise universe" >> /etc/apt/sources.list
 RUN apt-get update
 RUN apt-get install -y python git
 
 # Finally - we wanna be able to SSH in
 RUN apt-get install -y openssh-server
 RUN mkdir /var/run/sshd
 RUN echo 'root:screencast' | chpasswd
 
 # And we want our SSH key to be added
 RUN mkdir /root/.ssh && chmod 700 /root/.ssh
 ADD id_rsa.pub /root/.ssh/authorized_keys
 ADD id_rsa.pub /root/.ssh/id_rsa.pub
 ADD id_rsa /root/.ssh/id_rsa
 RUN chmod 400 /root/.ssh/authorized_keys && chown root:root /root/.ssh/* && chmod 600 /root/.ssh/*
 
 # Expose a bunch of ports .. 22 for SSH and 3000 for our node app
 EXPOSE 22 3000
 
 CMD /usr/sbin/sshd -D
