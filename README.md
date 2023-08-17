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
   $ go run client/main.go
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

  # Others
  ```
  go test ./cmd/... ./pkg/... -race -coverprofile=coverage.out -covermode=atomic
  go test ./pkg/ingress/... -race -coverprofile=coverage.out -covermode=atomic
  go test ./pkg/ingress/kube/annotations/... -race -coverprofile=coverage.out -covermode=atomic


  GENERATE_API=1 make gen-client

  docker build -t dubbo-provider-demo:0.0.1 . 

  docker build -t bazel-build:5.4.0 .

  docker tag dubbo-provider-demo:0.0.1 hisoka/dubbo-provider-demo:0.0.1

  docker run -it bazel-build:5.4.0

  docker run --name nacos-standlone -p 8848:8848 nacos-standlone:1.0.0-RC3

  kubectl config set-context --current --namespace=higress-system
  kubectl config set-context --current --namespace=kruise-system

  kind load docker-image dubbo-provider-demo:0.0.1 -n higress
  kind load docker-image dubbo-provider-demo:0.0.x -n higress
  kind load docker-image nacos-standlone:1.0.0-RC3 -n higress

  kubectl apply -f workspace/k8s/nacos/nacos-1.0.0-RC3-pod.yaml
  kubectl apply -f workspace/k8s/dubbo/demo-provider/demo-provider-pod.yaml

  kubectl logs higress-controller-5d56fb5459-z7hnf higress-core -n higress-system
  kubectl logs higress-gateway-667799d88f-6n4f6 -n higress-system
  kubectl logs dubbo-demo-provider -n higress-system
  kubectl logs grpc-server-demo -n higress-system


  kubectl exec -it higress-controller-7c4549cc84-xgf7s -n higress-system -- curl localhost:15014/debug/registryz
  kubectl exec -it higress-controller-5d56fb5459-9xggq -c higress-core -n higress-system -- curl localhost:15014/debug/configz
  kubectl exec -it higress-gateway-667799d88f-6n4f6 -n higress-system -- /bin/sh
  kubectl exec -it grpc-server-demo -n higress-system -- /bin/sh

  kubectl port-forward nacos-standlone-rc3 8848:8848
  kubectl port-forward grpc-server-demo 50051:50051

  进gateway容器，curl localhost:15020/stats/prometheus，有个指标 envoy_wasm_envoy_wasm_runtime_v8_active 是活跃的插件 vm 数

  ping nacos-standlone-rc3-service.higress-system.pod.cluster.local


  protoc -I/Users/h/workspace/project/github/googleapis -I. --include_imports --include_source_info --descriptor_set_out=proto.pb helloworld/helloworld.proto

  brew install protobuf

  protoc -I${GOOGLEAPIS_DIR} -I. --include_imports --include_source_info --descriptor_set_out=proto.pb helloworld/helloworld.proto
  ```