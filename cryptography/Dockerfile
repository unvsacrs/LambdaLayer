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

RUN sudo amazon-linux-extras install -y python3.8

RUN echo 'alias python=python3.8' >> ~/.bashrc
RUN source ~/.bashrc

RUN python -V

RUN pip3.8 install --upgrade pip

WORKDIR "${LAMBDA_TASK_ROOT}"

COPY requirements.txt  .

RUN  pip3.8 install -r requirements.txt --target python

RUN  zip -r cryptography.zip python

ARG AWS_ACCESS_KEY_ID
ARG AWS_SECRET_ACCESS_KEY
ARG AWS_S3_NAME

RUN  aws s3 cp cryptography.zip s3://${AWS_S3_NAME}/
