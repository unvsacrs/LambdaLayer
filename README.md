# LambdaLayer生成用 DockerFile

## Python3.8用とPython3.11用に分かれています

### ビルド方法
### docker build --build-arg AWS_ACCESS_KEY_ID=[アクセスキーID] --build-arg AWS_SECRET_ACCESS_KEY=[シークレットアクセスキー] --build-arg AWS_S3_NAME=[バケット名/キー名] ./