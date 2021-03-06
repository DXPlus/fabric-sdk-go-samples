## Fabric-SDK-Go的安装与使用教程

- 使用Fabric官方示例Build-Your-Frist-Network所构建的Fabric网络
- Fabric版本为fabric v1.4.1
- 本教程适用于Linux和MacOS

### 一. 安装Go环境和Docker

1. [安装Go并配置环境变量](https://www.cnblogs.com/jxxiaocao/p/12175954.html)
2. [安装Docker和Docker-compose](https://learnku.com/articles/29690)

### 二. 下载Fabric的Docker镜像

1. 下载fabric-samples项目源码

   ```bash
   cd $GOPATH
   mkdir -p src/github.com/hyperledger
   cd $GOPATH/src/github.com/hyperledger
   git clone https://github.com/hyperledger/fabric-samples.git
   ```

2. 执行脚本获取指定版本的fabric镜像文件

   ```bash
   cd scripts
   ./bootstrap.sh 1.4.1 1.4.1 0.4.15
   ```

   注意：如果提示权限不够，添加权限

   ```bash
   chmod +x bootstrap.sh
   ```

   该脚本已经将fabric所需的二进制文件放在fabric-samples/bin目录中，需要将文件复制到/usr/local/bin目录下

   ```bash
   cd $GOPATH/src/github.com/hyperledger/fabric-samples/bin
   cp cryptogen configtxlator configtxgen /usr/local/bin
   ```

### 三. 创建部署Fabric网络

构建你的第一个网络（BYFN）场景，提供了由两个组织组成的示例Hyperledger Fabric网络，每个组织持有2个peer节点，以及一个“solo”排序服务。

1. 进入fabric-samples/first-network下执行部署脚本

   ```bash
   cd fabric-samples/first-network
   ./byfn.sh -m generate
   ./byfn.sh -m up
   ```

   ./byfn.sh -m generate：生成我们各种网络实体的所有证书和密钥

   ./byfn.sh -m up：启动fabric网络

   ./byfn.sh -m down：关闭清除fabric网络

2. 如需关闭fabric网络

   ```
   ./byfn.sh -m down
   ```

   注意：在./byfn.sh -m up执行失败时，执行./byfn.sh -m down后，再次执行./byfn.sh -m up即可



### 四. 运行Fabric-SDK-Go-Samples

1. 下载Fabric-SDK-Go-Samples源码
2. 下载源码的相关依赖项
3. 修改部分配置文件
4. 运行示例与fabric网络交互
