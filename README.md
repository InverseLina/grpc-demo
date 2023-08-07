# gRPC Hello World

## Run ant test it at local
Follow these setup to run the [quick start][] example:

 1. Get the code:

    ```console
    $ go get google.golang.org/grpc/grpc-demo/client
    $ go get google.golang.org/grpc/grpc-demo/server
    ```

 2. Run the server:

    ```console
    $ $(go env GOPATH)/bin/server &
    ```

 3. Run the client:

    ```console
    $ $(go env GOPATH)/bin/client
    Greeting: Hello world
    ```

For more details (including instructions for making a small change to the
example code) or if you're having trouble running this example, see [Quick
Start][].

[quick start]: https://grpc.io/docs/languages/go/quickstart

## Run with Docker

 1. build grpc-demo server app
 
   ```console
   $ docker build -t grpc-demo-server:0.0.1 -f Dockerfile_Server .
   ```
 2. run grpc-demo server app  with docker 
 
   ```console
   $ docker run -d -p 50051:50051 grpc-demo-server:0.0.1
   ```
 3. run grpc-demo client app to test service service
 
   ```console
   $ go run server/main.go
   ```

## Run with K8S

 1. build grpc-demo server app
 
   ```console
   $ docker build -t grpc-demo-server:0.0.1 -f Dockerfile_Server .
   ```
 2. run grpc-demo server app  with docker 
 
   ```console
   $ docker run -d -p 50051:50051 grpc-demo-server:0.0.1
   ```
 3. run grpc-demo client app to test service service
 
   ```console
   $ go run client/main.go
   ```

## Build docker image tag and push aliyun

  1. 登录阿里云Docker Registry
  ```
  $ docker login --username=hins****@163.com registry.cn-hangzhou.aliyuncs.com
  ```
  用于登录的用户名为阿里云账号全名，密码为开通服务时设置的密码。
  您可以在访问凭证页面修改凭证密码。

  2. 从Registry中拉取镜像
  ```
  $ docker pull registry.cn-hangzhou.aliyuncs.com/hinsteny/grpc-demo-server:[镜像版本号]
  ```
  3. 将镜像推送到Registry
  ```
  $ docker login --username=hins****@163.com registry.cn-hangzhou.aliyuncs.com
  $ docker tag [ImageId] registry.cn-hangzhou.aliyuncs.com/hinsteny/grpc-demo-server:[镜像版本号]
  $ docker push registry.cn-hangzhou.aliyuncs.com/hinsteny/grpc-demo-server:[镜像版本号]
  ```
  请根据实际镜像信息替换示例中的[ImageId]和[镜像版本号]参数。