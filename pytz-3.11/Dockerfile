FROM  unvsacrs/lambda-layer-3.11:latest

ARG AWS_ACCESS_KEY_ID
ARG AWS_SECRET_ACCESS_KEY

WORKDIR "${LAMBDA_TASK_ROOT}"

COPY requirements.txt  .

RUN rm -fR python

RUN mkdir python

RUN  pip3.11 install -r requirements.txt --target python

RUN  zip -r pytz-311.zip python

RUN  aws s3 cp pytz-311.zip s3://toa-lambda-layers/
