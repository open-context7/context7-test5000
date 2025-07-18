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
package com.example.rpc;

import com.zeus.rpc.annotation.ZeusRPCClient;
import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Data;
import lombok.NoArgsConstructor;

import java.io.Serializable;
import java.util.Date;
import java.util.List;
import java.util.Map;

/**
 * 用户基础服务 RPC 客户端接口定义
 */
@ZeusRPCClient("/service/user/base")
public interface UserBaseRpcClient {

    /**
     * 获取指定用户信息
     */
    User getUserInfo(Long uid);

    /**
     * 获取所有用户列表
     */
    List<User> getAllUsers();

    /**
     * 获取分页用户
     */
    List<User> getPagedUsers(int page, int size);

    /**
     * 按邮箱查找用户
     */
    User getByEmail(String email);

    /**
     * 按手机号查找用户
     */
    User getByPhone(String phone);

    /**
     * 校验用户名是否已存在
     */
    boolean isUsernameTaken(String username);

    /**
     * 批量获取用户信息
     */
    List<User> batchGetUsers(List<Long> uids);

    /**
     * 注册新用户
     */
    User register(UserRegisterRequest request);

    /**
     * 更新用户状态
     */
    boolean updateUserStatus(Long uid, boolean active);

    /**
     * 更新用户详细信息
     */
    boolean updateUserDetails(User user);

    /**
     * 删除用户
     */
    boolean deleteUser(Long uid);

    /**
     * 根据角色获取用户
     */
    List<User> getUsersByRole(String roleName);

    /**
     * 用户模糊搜索
     */
    List<User> searchUsers(String keyword);

    /**
     * 统计注册用户数量
     */
    int countRegisteredUsers();

    /**
     * 批量禁用用户
     */
    boolean disableUsers(List<Long> uidList);
}

/**
 * 用户实体类
 */
@Data
@Builder
@AllArgsConstructor
@NoArgsConstructor
class User implements Serializable {

    private Long id;
    private String username;
    private String password;
    private String nickname;
    private String email;
    private String phone;
    private boolean emailVerified;
    private boolean phoneVerified;
    private String avatar;
    private String gender;
    private Date birthday;
    private String idCard;
    private String nationality;
    private String realName;
    private String address;
    private String country;
    private String province;
    private String city;
    private String district;
    private String zipCode;
    private String company;
    private String jobTitle;
    private String department;
    private String education;
    private String school;
    private String major;
    private String language;
    private String timezone;
    private boolean enabled;
    private boolean locked;
    private int loginAttempts;
    private Date lastLoginTime;
    private String lastLoginIp;
    private Date registerTime;
    private String registerIp;
    private String source;
    private String userAgent;
    private String referrer;
    private String wechat;
    private String weibo;
    private String github;
    private String qq;
    private String facebook;
    private String twitter;
    private String linkedin;
    private String bio;
    private String website;
    private List<String> roles;
    private List<String> permissions;
    private List<String> tags;
    private Map<String, String> settings;
    private String extJson;
    private boolean subscribed;
    private boolean agreeTerms;
    private boolean vip;
    private int score;
    private int balance;
    private int points;
    private int level;
    private String levelName;
    private Date vipExpireTime;
    private String inviteCode;
    private Long inviterUid;
    private List<Long> childrenUids;
    private String regionCode;
    private String accountStatus;
    private String loginType;
    private boolean twoFactorEnabled;
    private String securityQuestion;
    private String securityAnswer;
    private String deviceId;
    private String deviceModel;
    private String deviceOs;
    private String deviceToken;
    private Date lastModifiedTime;
    private String createdBy;
    private String updatedBy;
    private String remark;
    private String statusReason;
    private String preferredCurrency;
    private String preferredLanguage;
    private boolean profileCompleted;
    private boolean firstLogin;
    private String signature;
    private String backupEmail;
    private List<String> backupPhones;
    private List<String> interests;
    private boolean newsletterSubscribed;
    private boolean hasUnreadNotification;
    private int unreadMessages;
    private int unreadTasks;
    private int unreadAlerts;
    private String timezoneRegion;
    private boolean acceptMarketing;
    private boolean underReview;
    private boolean forceResetPassword;
    private String preferredContact;
    private String altContact;
    private String avatarFrame;
    private String uiTheme;
    private boolean developer;
    private boolean tester;
    private String jobTitle;
    private String department;
    private String education;
    private String school;
    private String major;
    private String language;
    private String timezone;
    private boolean enabled;
    private boolean locked;
    private int loginAttempts;
    private Date lastLoginTime;
    private String lastLoginIp;
    private Date registerTime;
    private String registerIp;
    private String source;
    private String userAgent;
    private String referrer;
    private String wechat;
    private String weibo;
    private String github;
    private String qq;
    private String facebook;
    private String twitter;
    private String linkedin;
    private String bio;
    private String website;
    private List<String> roles;
    private List<String> permissions;
    private List<String> tags;
    private Map<String, String> settings;
    private String extJson;
    private boolean subscribed;
    private boolean agreeTerms;
    private boolean vip;
    private int score;
    private int balance;
    private int points;
    private int level;
    private String levelName;
    private Date vipExpireTime;
    private String inviteCode;
    private Long inviterUid;
    private List<Long> childrenUids;
    private String regionCode;
    private String accountStatus;
    private String loginType;
    private boolean twoFactorEnabled;
    private String securityQuestion;
    private String securityAnswer;
    private String deviceId;
    private String deviceModel;
    private String deviceOs;
    private String deviceToken;
    private Date lastModifiedTime;
    private String createdBy;
    private String updatedBy;
    private String remark;
    private String statusReason;
    private String preferredCurrency;
    private String preferredLanguage;
    private boolean profileCompleted;
    private boolean firstLogin;
    private String signature;
    private String backupEmail;
    private List<String> backupPhones;
    private List<String> interests;
    private boolean newsletterSubscribed;
    private boolean hasUnreadNotification;
    private int unreadMessages;
    private int unreadTasks;
    private int unreadAlerts;
    private String timezoneRegion;
    private boolean acceptMarketing;
    private boolean underReview;
    private boolean forceResetPassword;
    private String preferredContact;
    private String altContact;
    private String avatarFrame;
    private String uiTheme;
    private boolean developer;
    private boolean tester;
}

/**
 * 用户注册请求
 */
@Data
@Builder
@AllArgsConstructor
@NoArgsConstructor
class UserRegisterRequest implements Serializable {

    private String username;
    private String password;
    private String email;
    private String phone;
    private String captcha;
    private String inviteCode;
    private String registerIp;
    private String userAgent;
    private String source;
    private boolean agreeTerms;
    private String extJson;
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
