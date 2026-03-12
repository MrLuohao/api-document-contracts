# WechatPlatformInformationController 接口文档

## Controller 基本信息

| 项目 | 内容 |
|------|------|
| 域 | `user` |
| 服务名 | `dst-user-core-service` |
| 接口层级 | `innerapi` |
| Controller | `WechatPlatformInformationController` |
| 基础路径 | `/v2/wechat` |
| Controller owner | `luohao` |

---

## 1. 获取用户在企业开放平台的所有相关信息

### 1.1 基本信息

| 项目 | 内容 |
|------|------|
| operationId | `user.innerapi.aiAgent.getAllInformation` |
| 请求方法 | `POST` |
| 请求路径 | `/v2/wechat/getAll` |
| 简要描述 | `执行Getall并返回AllInformation` |

### 1.2 请求参数

#### Body 参数

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `unionId` | `String` | ❌ | 微信开放平台用户唯一标识 |
| `openId` | `String` | ❌ | 用户在单个应用的唯一标识符 |
| `phone` | `String` | ❌ | 电话 |

### 1.3 响应结构

| 项目 | 内容 |
|------|------|
| 统一包装 | `com.dst.steed.common.domain.response.Response` |
| data 类型 | `AllInformationDTO` |
| 说明 | `Getall执行结果` |

### 1.4 Feign Client 定义

```java
@FeignClient(name = "dst-user-core-service", contextId = "WechatPlatformInformationClientApi")
public interface WechatPlatformInformationClientApi {

    @PostMapping("/v2/wechat/getAll")
    Response<AllInformationDTO> getAllInformation(@RequestBody FindInformationParam query);
}
```

### 1.5 DTO 定义

#### FindInformationParam

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `unionId` | `String` | ❌ | 微信开放平台用户唯一标识 |
| `openId` | `String` | ❌ | 用户在单个应用的唯一标识符 |
| `phone` | `String` | ❌ | 电话 |

#### AllInformationDTO

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `openPlatforms` | `List<WechatOpenPlatform>` | ❌ | 用户在企业微信开放平台相关信息 |
| `externalContactRelations` | `List<ExternalContactRelation>` | ❌ | 用户在企业微信中所添加的所有内部成员相关信息 |
| `externalGroupRelations` | `List<ExternalGroupRelation>` | ❌ | 用户在企业微信中所添加的所有内部群相关信息 |

#### WechatOpenPlatform

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `creatorId` | `Long` | ❌ |  |
| `creatorName` | `String` | ❌ |  |
| `createTime` | `Date` | ❌ |  |
| `modifierId` | `Long` | ❌ |  |
| `modifierName` | `String` | ❌ |  |
| `modifyTime` | `Date` | ❌ |  |
| `id` | `Long` | ❌ | 主键 |
| `appId` | `String` | ❌ | 应用的唯一标识符 |
| `openId` | `String` | ❌ | 用户在单个应用的唯一标识符 |
| `userId` | `Long` | ❌ | 用户id |
| `unionId` | `String` | ❌ | 微信开放平台用户唯一标识 |
| `phone` | `String` | ❌ | 手机号 |
| `phoneMask` | `String` | ❌ | 手机号掩码 |
| `phoneEncrypt` | `String` | ❌ | 手机号加密 |
| `channel` | `String` | ❌ | 渠道 |

#### BaseDO

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `creatorId` | `Long` | ❌ |  |
| `creatorName` | `String` | ❌ |  |
| `createTime` | `Date` | ❌ |  |
| `modifierId` | `Long` | ❌ |  |
| `modifierName` | `String` | ❌ |  |
| `modifyTime` | `Date` | ❌ |  |

#### ExternalContactRelation

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `id` | `Long` | ❌ | 主键ID |
| `externalUserid` | `String` | ❌ | 外部客户的openID |
| `unionId` | `String` | ❌ | 外部联系人在微信开放平台的唯一身份标识 |
| `nickName` | `String` | ❌ | 微信昵称或企业微信对外展示名 |
| `gender` | `Integer` | ❌ | 性别 0-未知 1-男性 2-女性 |
| `avatar` | `String` | ❌ | 头像 |
| `type` | `Integer` | ❌ | 外部联系人类型 1-微信用户 2-企业微信用户 |
| `corpName` | `String` | ❌ | 外部联系人所在企业的简称 |
| `followUserId` | `String` | ❌ | 跟进人的userid |
| `followUserRemark` | `String` | ❌ | 成员对客户的备注 |
| `followUserDescription` | `String` | ❌ | 成员对客户的描述 |
| `followUserCreateTime` | `Date` | ❌ | 添加客户时间 |
| `followUserRemarkMobiles` | `String` | ❌ | 备注的手机号码 |
| `followUserAddWay` | `Integer` | ❌ | 添加来源 (来源定义查看企业微信官方文档) |
| `locked` | `Integer` | ❌ | 状态 0-正常 1-已删除 |

#### ExternalGroupRelation

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `id` | `Long` | ❌ | 主键ID |
| `memberUserid` | `String` | ❌ | 群成员id(external_userid) |
| `unionId` | `String` | ❌ | 外部联系人在微信开放平台的唯一身份标识 |
| `chatId` | `String` | ❌ | 客户群ID |
| `chatName` | `String` | ❌ | 群名 |
| `chatOwner` | `String` | ❌ | 群主ID |
| `chatCreateTime` | `Date` | ❌ | 群的创建时间 |
| `memberType` | `Integer` | ❌ | 成员类型 1-企业成员 2-外部联系人 |
| `memberJoinTime` | `Date` | ❌ | 入群时间 |
| `memberJoinScene` | `Integer` | ❌ | 入群方式 1-直接邀请 2-链接入群 3-扫码入群 |
| `memberInvitorUserid` | `String` | ❌ | 邀请者userid |
| `memberGroupNickname` | `String` | ❌ | 群昵称 |
| `memberName` | `String` | ❌ | 展示名称 (微信昵称) |
| `adminList` | `String` | ❌ | 群管理员列表 |
| `memberVersion` | `String` | ❌ | 群成员版本号 |
| `locked` | `Integer` | ❌ | 状态 0-正常 1-已删除 |

### 1.6 示例

```json
null
```

### 1.7 业务校验规则

无业务错误定义。

### 1.8 源码定位

| 项目 | 内容 |
|------|------|
| 源码文件 | `src/main/java/com/dst/user/core/modules/innerapi/weixin/controller/WechatPlatformInformationController.java` |
| 方法签名 | `getAllInformation(FindInformationParam param)` |
| 接口 owner | `luohao` |

---

## 2. 删除重复的openId

### 2.1 基本信息

| 项目 | 内容 |
|------|------|
| operationId | `user.innerapi.aiAgent.delRepeatOpenId` |
| 请求方法 | `POST` |
| 请求路径 | `/v2/wechat/del` |
| 简要描述 | `执行Del并返回Object` |

### 2.2 请求参数

无请求参数。

### 2.3 响应结构

| 项目 | 内容 |
|------|------|
| 统一包装 | `com.dst.steed.common.domain.response.Response` |
| data 类型 | `Object` |
| 说明 | `Del执行结果` |

### 2.4 Feign Client 定义

```java
@FeignClient(name = "dst-user-core-service", contextId = "WechatPlatformInformationClientApi")
public interface WechatPlatformInformationClientApi {

    @PostMapping("/v2/wechat/del")
    Response<Object> delRepeatOpenId();
}
```

### 2.5 DTO 定义

### 2.6 示例

```json
null
```

### 2.7 业务校验规则

无业务错误定义。

### 2.8 源码定位

| 项目 | 内容 |
|------|------|
| 源码文件 | `src/main/java/com/dst/user/core/modules/innerapi/weixin/controller/WechatPlatformInformationController.java` |
| 方法签名 | `delRepeatOpenId()` |
| 接口 owner | `luohao` |

---

## 3. 同步某个公众号端所有用户的openID + union ID

### 3.1 基本信息

| 项目 | 内容 |
|------|------|
| operationId | `user.innerapi.aiAgent.getOfficialAccountAdmins` |
| 请求方法 | `GET` |
| 请求路径 | `/v2/wechat/getOfficialAccountAdmins` |
| 简要描述 | `查询Getofficialaccountadmins详情并返回Object` |

### 3.2 请求参数

#### Query 参数

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `appId` | `String` | ✅ | appId |


### 3.3 响应结构

| 项目 | 内容 |
|------|------|
| 统一包装 | `com.dst.steed.common.domain.response.Response` |
| data 类型 | `Object` |
| 说明 | `Getofficialaccountadmins详情` |

### 3.4 Feign Client 定义

```java
@FeignClient(name = "dst-user-core-service", contextId = "WechatPlatformInformationClientApi")
public interface WechatPlatformInformationClientApi {

    @GetMapping("/v2/wechat/getOfficialAccountAdmins")
    Response<Object> getOfficialAccountAdmins(@RequestParam(value = "appId", required = true) String appId);
}
```

### 3.5 DTO 定义

### 3.6 示例

```json
{"appId":"value"}
```

### 3.7 业务校验规则

无业务错误定义。

### 3.8 源码定位

| 项目 | 内容 |
|------|------|
| 源码文件 | `src/main/java/com/dst/user/core/modules/innerapi/weixin/controller/WechatPlatformInformationController.java` |
| 方法签名 | `getOfficialAccountAdmins(String appId)` |
| 接口 owner | `luohao` |

---

## 4. 记录企业微信端用户的External_userID + Union ID

### 4.1 基本信息

| 项目 | 内容 |
|------|------|
| operationId | `user.innerapi.aiAgent.getWeComAdminInformation` |
| 请求方法 | `POST` |
| 请求路径 | `/v2/wechat/getWeComAdminInformation` |
| 简要描述 | `执行Getwecomadmininformation并返回Object` |

### 4.2 请求参数

#### Body 参数

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `corpName` | `String` | ✅ | 企微绑定的应用名称 |

### 4.3 响应结构

| 项目 | 内容 |
|------|------|
| 统一包装 | `com.dst.steed.common.domain.response.Response` |
| data 类型 | `Object` |
| 说明 | `Getwecomadmininformation执行结果` |

### 4.4 Feign Client 定义

```java
@FeignClient(name = "dst-user-core-service", contextId = "WechatPlatformInformationClientApi")
public interface WechatPlatformInformationClientApi {

    @PostMapping("/v2/wechat/getWeComAdminInformation")
    Response<Object> getWeComAdminInformation(@RequestBody WeComInformationParam query);
}
```

### 4.5 DTO 定义

#### WeComInformationParam

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `corpName` | `String` | ✅ | 企微绑定的应用名称 |

### 4.6 示例

```json
null
```

### 4.7 业务校验规则

无业务错误定义。

### 4.8 源码定位

| 项目 | 内容 |
|------|------|
| 源码文件 | `src/main/java/com/dst/user/core/modules/innerapi/weixin/controller/WechatPlatformInformationController.java` |
| 方法签名 | `getWeComAdminInformation(WeComInformationParam param)` |
| 接口 owner | `luohao` |

---

## 5. 获取因内部成员离职待分配的外部客户信息

### 5.1 基本信息

| 项目 | 内容 |
|------|------|
| operationId | `user.innerapi.aiAgent.getUnassignedList` |
| 请求方法 | `POST` |
| 请求路径 | `/v2/wechat/getUnassignedList` |
| 简要描述 | `执行Getunassignedlist并返回HandoverToBeAllocated` |

### 5.2 请求参数

#### Body 参数

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `corpName` | `String` | ✅ | 企微绑定的应用名称 |

### 5.3 响应结构

| 项目 | 内容 |
|------|------|
| 统一包装 | `com.dst.steed.common.domain.response.Response` |
| data 类型 | `HandoverToBeAllocatedDTO` |
| 说明 | `Getunassignedlist执行结果` |

### 5.4 Feign Client 定义

```java
@FeignClient(name = "dst-user-core-service", contextId = "WechatPlatformInformationClientApi")
public interface WechatPlatformInformationClientApi {

    @PostMapping("/v2/wechat/getUnassignedList")
    Response<HandoverToBeAllocatedDTO> getUnassignedList(@RequestBody WeComInformationParam query);
}
```

### 5.5 DTO 定义

#### WeComInformationParam

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `corpName` | `String` | ✅ | 企微绑定的应用名称 |

#### HandoverToBeAllocatedDTO

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `handoverUserIdCnt` | `Integer` | ❌ | @Author: 罗豪@CreateTime: 2025-04-18@Description: 内部成员离职、外部客户待分配信息 |
| `externalUserIdCnt` | `Integer` | ❌ |  |
| `handoverUserIds` | `List<String>` | ❌ |  |
| `externalUserIds` | `List<String>` | ❌ |  |

### 5.6 示例

```json
null
```

### 5.7 业务校验规则

无业务错误定义。

### 5.8 源码定位

| 项目 | 内容 |
|------|------|
| 源码文件 | `src/main/java/com/dst/user/core/modules/innerapi/weixin/controller/WechatPlatformInformationController.java` |
| 方法签名 | `getUnassignedList(WeComInformationParam param)` |
| 接口 owner | `luohao` |

---

## 6. 根据用户id 查询尘锋关联信息

### 6.1 基本信息

| 项目 | 内容 |
|------|------|
| operationId | `user.innerapi.aiAgent.getContact` |
| 请求方法 | `POST` |
| 请求路径 | `/v2/wechat/getByUserId` |
| 简要描述 | `执行Getbyuserid并返回DustEdgeRelation` |

### 6.2 请求参数

#### Body 参数

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `userIds` | `List<String>` | ✅ | 车上云用户 ID |

### 6.3 响应结构

| 项目 | 内容 |
|------|------|
| 统一包装 | `com.dst.steed.common.domain.response.Response` |
| data 类型 | `List<DustEdgeRelationVO>` |
| 说明 | `Getbyuserid执行结果` |

### 6.4 Feign Client 定义

```java
@FeignClient(name = "dst-user-core-service", contextId = "WechatPlatformInformationClientApi")
public interface WechatPlatformInformationClientApi {

    @PostMapping("/v2/wechat/getByUserId")
    Response<List<DustEdgeRelationVO>> getContact(@RequestBody DustEdgeRelationQuery query);
}
```

### 6.5 DTO 定义

#### DustEdgeRelationQuery

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `userIds` | `List<String>` | ✅ | 车上云用户 ID |

#### DustEdgeRelationVO

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `userId` | `Long` | ❌ | 用户 id |
| `customerId` | `String` | ❌ | 尘锋 customer_id |
| `unionId` | `String` | ❌ | 外部联系人在微信开放平台的唯一身份标识 |

### 6.6 示例

```json
null
```

### 6.7 业务校验规则

无业务错误定义。

### 6.8 源码定位

| 项目 | 内容 |
|------|------|
| 源码文件 | `src/main/java/com/dst/user/core/modules/innerapi/weixin/controller/WechatPlatformInformationController.java` |
| 方法签名 | `getContact(DustEdgeRelationQuery query)` |
| 接口 owner | `hongweisheng` |

---

## 7. 从给定的跟进人列表中，返回添加外部联系人最少的跟进人 user_id

### 7.1 基本信息

| 项目 | 内容 |
|------|------|
| operationId | `user.innerapi.aiAgent.getFollowUserId` |
| 请求方法 | `POST` |
| 请求路径 | `/v2/wechat/getFollowUserId` |
| 简要描述 | `执行Getfollowuserid并返回MinFollowUserId` |

### 7.2 请求参数

#### Body 参数

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `followUserIds` | `List<String>` | ✅ | 跟进人 userid列表 |
| `corpName` | `String` | ❌ | 企业微信企业名称（可选）用于获取对应企业的access_token如果不传，则使用配置中的第一个企业 |

### 7.3 响应结构

| 项目 | 内容 |
|------|------|
| 统一包装 | `com.dst.steed.common.domain.response.Response` |
| data 类型 | `MinFollowUserIdDTO` |
| 说明 | `Getfollowuserid执行结果` |

### 7.4 Feign Client 定义

```java
@FeignClient(name = "dst-user-core-service", contextId = "WechatPlatformInformationClientApi")
public interface WechatPlatformInformationClientApi {

    @PostMapping("/v2/wechat/getFollowUserId")
    Response<MinFollowUserIdDTO> getFollowUserId(@RequestBody FollowUserIdsParam query);
}
```

### 7.5 DTO 定义

#### FollowUserIdsParam

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `followUserIds` | `List<String>` | ✅ | 跟进人 userid列表 |
| `corpName` | `String` | ❌ | 企业微信企业名称（可选）用于获取对应企业的access_token如果不传，则使用配置中的第一个企业 |

#### MinFollowUserIdDTO

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `followUserId` | `String` | ❌ | 跟进人user_id |
| `qrCodeUrl` | `String` | ❌ | 企业微信「联系我」二维码链接客户扫描此二维码可添加该跟进人 |

### 7.6 示例

```json
null
```

### 7.7 业务校验规则

无业务错误定义。

### 7.8 源码定位

| 项目 | 内容 |
|------|------|
| 源码文件 | `src/main/java/com/dst/user/core/modules/innerapi/weixin/controller/WechatPlatformInformationController.java` |
| 方法签名 | `getFollowUserId(FollowUserIdsParam param)` |
| 接口 owner | `luohao` |

---

## 8. 为外部联系人（客户）打标签

### 8.1 基本信息

| 项目 | 内容 |
|------|------|
| operationId | `user.innerapi.aiAgent.markTag` |
| 请求方法 | `POST` |
| 请求路径 | `/v2/wechat/markTag` |
| 简要描述 | `执行Marktag并返回Object` |

### 8.2 请求参数

#### Body 参数

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `corpName` | `String` | ❌ | 企业名称（可选）用于获取对应企业的access_token如果不传，则使用配置中的第一个企业 |
| `userid` | `String` | ✅ | 添加外部联系人的企业成员userid必填 |
| `external_userid` | `String` | ✅ | 外部联系人userid必填 |
| `add_tag` | `List<String>` | ❌ | 要添加的标签ID列表add_tag和remove_tag不可同时为空 |
| `remove_tag` | `List<String>` | ❌ | 要移除的标签ID列表add_tag和remove_tag不可同时为空 |

### 8.3 响应结构

| 项目 | 内容 |
|------|------|
| 统一包装 | `com.dst.steed.common.domain.response.Response` |
| data 类型 | `Object` |
| 说明 | `Marktag执行结果` |

### 8.4 Feign Client 定义

```java
@FeignClient(name = "dst-user-core-service", contextId = "WechatPlatformInformationClientApi")
public interface WechatPlatformInformationClientApi {

    @PostMapping("/v2/wechat/markTag")
    Response<Object> markTag(@RequestBody MarkTagParam query);
}
```

### 8.5 DTO 定义

#### MarkTagParam

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `corpName` | `String` | ❌ | 企业名称（可选）用于获取对应企业的access_token如果不传，则使用配置中的第一个企业 |
| `userid` | `String` | ✅ | 添加外部联系人的企业成员userid必填 |
| `external_userid` | `String` | ✅ | 外部联系人userid必填 |
| `add_tag` | `List<String>` | ❌ | 要添加的标签ID列表add_tag和remove_tag不可同时为空 |
| `remove_tag` | `List<String>` | ❌ | 要移除的标签ID列表add_tag和remove_tag不可同时为空 |

### 8.6 示例

```json
null
```

### 8.7 业务校验规则

无业务错误定义。

### 8.8 源码定位

| 项目 | 内容 |
|------|------|
| 源码文件 | `src/main/java/com/dst/user/core/modules/innerapi/weixin/controller/WechatPlatformInformationController.java` |
| 方法签名 | `markTag(MarkTagParam param)` |
| 接口 owner | `luohao` |

---

## 9. 获取企业标签库列表

### 9.1 基本信息

| 项目 | 内容 |
|------|------|
| operationId | `user.innerapi.aiAgent.getCorpTagList` |
| 请求方法 | `POST` |
| 请求路径 | `/v2/wechat/getCorpTagList` |
| 简要描述 | `执行Getcorptaglist并返回Object` |

### 9.2 请求参数

#### Body 参数

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `corpName` | `String` | ❌ | 企业名称（可选）用于获取对应企业的access_token如果不传，则使用配置中的第一个企业 |
| `tag_id` | `List<String>` | ❌ | 标签组ID列表不传则获取全部标签组 |
| `group_id` | `List<String>` | ❌ | 标签组ID列表不传则获取全部标签组 |

### 9.3 响应结构

| 项目 | 内容 |
|------|------|
| 统一包装 | `com.dst.steed.common.domain.response.Response` |
| data 类型 | `Object` |
| 说明 | `Getcorptaglist执行结果` |

### 9.4 Feign Client 定义

```java
@FeignClient(name = "dst-user-core-service", contextId = "WechatPlatformInformationClientApi")
public interface WechatPlatformInformationClientApi {

    @PostMapping("/v2/wechat/getCorpTagList")
    Response<Object> getCorpTagList(@RequestBody GetCorpTagListParam query);
}
```

### 9.5 DTO 定义

#### GetCorpTagListParam

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `corpName` | `String` | ❌ | 企业名称（可选）用于获取对应企业的access_token如果不传，则使用配置中的第一个企业 |
| `tag_id` | `List<String>` | ❌ | 标签组ID列表不传则获取全部标签组 |
| `group_id` | `List<String>` | ❌ | 标签组ID列表不传则获取全部标签组 |

### 9.6 示例

```json
null
```

### 9.7 业务校验规则

无业务错误定义。

### 9.8 源码定位

| 项目 | 内容 |
|------|------|
| 源码文件 | `src/main/java/com/dst/user/core/modules/innerapi/weixin/controller/WechatPlatformInformationController.java` |
| 方法签名 | `getCorpTagList(GetCorpTagListParam param)` |
| 接口 owner | `luohao` |

---

## 10. 用于在生产环境验证MQ发送是否正常，无需走完整流程

### 10.1 基本信息

| 项目 | 内容 |
|------|------|
| operationId | `user.innerapi.aiAgent.testExternalContactChangeMq` |
| 请求方法 | `POST` |
| 请求路径 | `/v2/wechat/test/externalContactChangeMq` |
| 简要描述 | `执行TestExternalcontactchangemq并返回Object` |

### 10.2 请求参数

#### Body 参数

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `externalUserid` | `String` | ❌ | 外部客户的externalUserid (日志中的creator字段) |
| `unionId` | `String` | ❌ | 外部联系人在微信开放平台的唯一身份标识 |
| `nickName` | `String` | ❌ | 微信昵称或企业微信对外展示名 |
| `gender` | `Integer` | ❌ | 性别 0-未知 1-男性 2-女性 |
| `avatar` | `String` | ❌ | 头像 |
| `type` | `Integer` | ❌ | 外部联系人类型 1-微信用户 2-企业微信用户 |
| `corpName` | `String` | ❌ | 外部联系人所在企业的简称 |
| `followUserId` | `String` | ❌ | 跟进人的userid |
| `followUserRemark` | `String` | ❌ | 成员对客户的备注 |
| `followUserDescription` | `String` | ❌ | 成员对客户的描述 |
| `followUserCreateTime` | `String` | ❌ | 添加客户时间 (格式: yyyy-MM-dd HH:mm:ss) |
| `followUserRemarkMobiles` | `String` | ❌ | 备注的手机号码 |
| `followUserAddWay` | `Integer` | ❌ | 添加来源 (来源定义查看企业微信官方文档) |
| `locked` | `Integer` | ❌ | 状态 0-正常 1-已删除 |
| `changeType` | `String` | ❌ | 变更类型 add/update |

### 10.3 响应结构

| 项目 | 内容 |
|------|------|
| 统一包装 | `com.dst.steed.common.domain.response.Response` |
| data 类型 | `Object` |
| 说明 | `TestExternalcontactchangemq执行结果` |

### 10.4 Feign Client 定义

```java
@FeignClient(name = "dst-user-core-service", contextId = "WechatPlatformInformationClientApi")
public interface WechatPlatformInformationClientApi {

    @PostMapping("/v2/wechat/test/externalContactChangeMq")
    Response<Object> testExternalContactChangeMq(@RequestBody ExternalContactTestParam query);
}
```

### 10.5 DTO 定义

#### ExternalContactTestParam

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `externalUserid` | `String` | ❌ | 外部客户的externalUserid (日志中的creator字段) |
| `unionId` | `String` | ❌ | 外部联系人在微信开放平台的唯一身份标识 |
| `nickName` | `String` | ❌ | 微信昵称或企业微信对外展示名 |
| `gender` | `Integer` | ❌ | 性别 0-未知 1-男性 2-女性 |
| `avatar` | `String` | ❌ | 头像 |
| `type` | `Integer` | ❌ | 外部联系人类型 1-微信用户 2-企业微信用户 |
| `corpName` | `String` | ❌ | 外部联系人所在企业的简称 |
| `followUserId` | `String` | ❌ | 跟进人的userid |
| `followUserRemark` | `String` | ❌ | 成员对客户的备注 |
| `followUserDescription` | `String` | ❌ | 成员对客户的描述 |
| `followUserCreateTime` | `String` | ❌ | 添加客户时间 (格式: yyyy-MM-dd HH:mm:ss) |
| `followUserRemarkMobiles` | `String` | ❌ | 备注的手机号码 |
| `followUserAddWay` | `Integer` | ❌ | 添加来源 (来源定义查看企业微信官方文档) |
| `locked` | `Integer` | ❌ | 状态 0-正常 1-已删除 |
| `changeType` | `String` | ❌ | 变更类型 add/update |

### 10.6 示例

```json
{}
```

### 10.7 业务校验规则

无业务错误定义。

### 10.8 源码定位

| 项目 | 内容 |
|------|------|
| 源码文件 | `src/main/java/com/dst/user/core/modules/innerapi/weixin/controller/WechatPlatformInformationController.java` |
| 方法签名 | `testExternalContactChangeMq(ExternalContactTestParam param)` |
| 接口 owner | `luohao` |
