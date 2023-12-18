# comfy-flow-api

这是一个ComfyUI的API聚合项目

1. 提供了工作流的API调用；
2. 提供了微信小程序的授权API；

## 配置

### 在 application.properties 文件中

我们需要修改如下配置

wechat.appid=小程序 appId
wechat.secret=小程序 appSecret

comfy.ips=ComfyUI所在服务器的IP，比如`127.0.0.1`

### 在 comfyui.json 文件中

我们需要修改如下配置

```json
[
  {
    "name": "工作流的名称，比如动漫风格转换",
    "path": "在服务器上，动漫风格转换的workflow-api.json所在的位置，比如/comfyui/workflow-api.json"
  }
]
```

## 本地测试

### 使用到的组件清单

可以访问地址: http://127.0.0.1:8189/q/dev-ui/extensions

![img.png](doc%2Fimg_0.png)

### 接口API清单

可以访问地址: http://127.0.0.1:8189/q/swagger-ui/

![img_1.png](doc%2Fimg_1.png)

### 简单使用

可以访问地址: http://127.0.0.1:8189/drawNow.html

![img_4.png](doc%2Fimg_4.png)

这个工作流使用到的资源如下

1. 模型: https://civitai.com/models/217692/mexxldimsdxllcm2?modelVersionId=245340
2. 插件1: https://github.com/SoftMeng/ComfyUI_Mexx_Styler

只是个流程测试，没有进度条。

## 部署（Jar包形式）

对项目进行打包

```shell script
./mvnw package -Dquarkus.package.type=uber-jar
```

打完包的程序在`target`中，安装JDK17或者21后，可以使用命令行启动

```shell
java -jar target/comfy-flow-api-runner.jar
```

## 部署（Native形式）

这需要你安装GraalVM

```shell script
./mvnw package -Dnative -Dquarkus.native.container-build=true
```

打包后可以使用下面命令启动

```shell
./target/comfy-flow-api-1.0.0-SNAPSHOT-runner
```