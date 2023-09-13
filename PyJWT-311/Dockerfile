FROM  unvsacrs/lambda-layer-3.11:latest

WORKDIR "${LAMBDA_TASK_ROOT}"

COPY requirements.txt  .

RUN rm -fR python

RUN mkdir python

RUN  pip3.11 install -r requirements.txt --target python

RUN  zip -r PyJWT-311.zip python

ARG AWS_ACCESS_KEY_ID
ARG AWS_SECRET_ACCESS_KEY
ARG AWS_S3_NAME

RUN  aws s3 cp PyJWT-311.zip s3://${AWS_S3_NAME}/
