FROM  --platform=linux/amd64 amazonlinux:2

# install amazon-linux-extras install
RUN amazon-linux-extras install -y

# yum update & install
RUN yum update -y \
    && yum install \
        systemd \
        tar \
        unzip \
        sudo \
        zip \
        -y

# install aws cli v2
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
    && unzip awscliv2.zip \
    && sudo ./aws/install

RUN yum remove openssl-devel
RUN yum install -y openssl11 openssl11-devel
RUN yum install gcc bzip2-devel libffi-devel zlib-devel -y wget make
RUN wget https://www.python.org/ftp/python/3.11.5/Python-3.11.5.tgz
RUN tar xzf Python-3.11.5.tgz 
WORKDIR Python-3.11.5
RUN ./configure --enable-optimizations
RUN make altinstall  
RUN rm -f /opt/Python-3.11.5.tgz 
RUN echo 'alias python=python3.11' >> ~/.bashrc
RUN echo 'alias pip=pip3.11' >> ~/.bashrc
RUN source ~/.bashrc

RUN python -V

RUN pip3.11 install --upgrade pip
