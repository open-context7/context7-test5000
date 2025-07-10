# zeus-rpc使用文档
## 介绍 
zeus-rpc包含两个模块：consumer与provider，
provider提供服务，通过封装zeus-common包对外暴露client接口，consumer通过client调用provider，
## 快速开始
### 定义client
#### 引用依赖
```groovy
implementation 'com.wb.zeus:zeus-common'
```
#### 创建Client
```shell
@ZeusRPCClient("/service/user/base")
public interface UserBaseRpcClient {
    /**
     * xxx
     */
    User getUserInfo(Long uid);
}

@Data
@Builder
@AllArgsConstructor
@NoArgsConstructor
public class User implements Serializable {
    private Integer id;
    private String name;
}
```
### 提供provider服务
#### 引用依赖
```groovy
//todo 依赖自己的client包 implementation project(":xxx-rpc-client")
implementation 'com.wb.zeus:zeus-rpc-starter'
```
#### 实现Client创建provider服务
```java
@ZeusService
public class UserBaseRpcService implements UserBaseRpcClient {
    public User getUserInfo(Long uid) {
        //...
    }
}
```
#### 配置yaml文件，启动zeus-rpc端口，scanPackages为UserBaseRpcService所在的包路径
```yaml
zeus:
  rpc:
    server:
      enabled : true
      scanPackages : "com.wb.xxx，必填"
```
### 通过zeus-rpc进行调用
#### 引用依赖（非spring项目）
```groovy
//依赖provider提供的client包 
implementation "com.wb.xxx:xxx-rpc-client:1.0-SNAPSHOT"
implementation 'com.wb.zeus:zeus-common'
```
#### 引用依赖（spring项目）
```groovy
//依赖provider提供的client包 
implementation "com.wb.xxx:xxx-rpc-client:1.0-SNAPSHOT"
implementation 'com.wb.zeus:zeus-rpc-starter'
```
#### 创建client并调用(非spring方式)
```java
UserBaseRpcClient userBaseRpcClient = ZeusRpcConsumerFactory.getInstance(UserBaseRpcClient.class);
```
#### 创建client并调用(spring方式)
```java
@ZeusReference
private UserBaseRpcClient userBaseRpcClient;
```
