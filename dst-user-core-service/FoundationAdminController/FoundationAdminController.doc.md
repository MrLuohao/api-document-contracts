# FoundationAdminController 接口文档

## Controller 基本信息

| 项目 | 内容 |
|------|------|
| 域 | `user-center` |
| 服务名 | `dst-user-core-service` |
| 接口层级 | `business` |
| Controller | `FoundationAdminController` |
| 基础路径 | `/foundation/admin` |
| Controller owner | `luohao` |

---

## 1. 修改个人用户信息(统一入口)

### 1.1 基本信息

| 项目 | 内容 |
|------|------|
| operationId | `user-center.business.aiAgent.modifyAdminInformation` |
| 请求方法 | `@RequestMapping` |
| 请求路径 | `/foundation/admin/modifyAdminInformation` |
| 简要描述 | `处理Modifyadmininformation并返回Object` |

### 1.2 请求参数

#### Body 参数

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `adminId` | `String` | ✅ | 用户ID |
| `realName` | `String` | ❌ | 用户姓名 |
| `urlFront` | `String` | ❌ | 身份证正面照片URL |
| `urlBack` | `String` | ❌ | 身份证反面照片URL |
| `cardId` | `String` | ❌ | 身份证号 |
| `channel` | `String` | ✅ | 接口调用方 |
| `modifierId` | `Long` | ❌ | 修改人id |
| `modifierName` | `String` | ❌ | 修改人名称 |
| `modifyTime` | `Date` | ❌ | 修改时间 |
| `jobNumber` | `String` | ❌ | 用户工号 |

### 1.3 响应结构

| 项目 | 内容 |
|------|------|
| 统一包装 | `com.dst.steed.common.domain.response.Response` |
| data 类型 | `Object` |
| 说明 | `Modifyadmininformation返回结果` |

### 1.4 Feign Client 定义

```java
@FeignClient(name = "dst-user-core-service", contextId = "FoundationAdminClientApi")
public interface FoundationAdminClientApi {

    @RequestMapping("/foundation/admin/modifyAdminInformation")
    Response<Object> modifyAdminInformation(@RequestBody ModifyAdminParam query);
}
```

### 1.5 DTO 定义

#### ModifyAdminParam

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `adminId` | `String` | ✅ | 用户ID |
| `realName` | `String` | ❌ | 用户姓名 |
| `urlFront` | `String` | ❌ | 身份证正面照片URL |
| `urlBack` | `String` | ❌ | 身份证反面照片URL |
| `cardId` | `String` | ❌ | 身份证号 |
| `channel` | `String` | ✅ | 接口调用方 |
| `modifierId` | `Long` | ❌ | 修改人id |
| `modifierName` | `String` | ❌ | 修改人名称 |
| `modifyTime` | `Date` | ❌ | 修改时间 |
| `jobNumber` | `String` | ❌ | 用户工号 |

### 1.6 示例

```json
null
```

### 1.7 业务校验规则

无业务错误定义。

### 1.8 源码定位

| 项目 | 内容 |
|------|------|
| 源码文件 | `src/main/java/com/dst/user/core/modules/business/foundation/controller/FoundationAdminController.java` |
| 方法签名 | `modifyAdminInformation(ModifyAdminParam param)` |
| 接口 owner | `luohao` |

---

## 2. 根据用户ID修改个人用户工号

### 2.1 基本信息

| 项目 | 内容 |
|------|------|
| operationId | `user-center.business.aiAgent.modifyJobNumber` |
| 请求方法 | `@RequestMapping` |
| 请求路径 | `/foundation/admin/modifyJobNumber` |
| 简要描述 | `处理Modifyjobnumber并返回Object` |

### 2.2 请求参数

#### Body 参数

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `adminId` | `String` | ✅ | 用户ID |
| `realName` | `String` | ❌ | 用户姓名 |
| `urlFront` | `String` | ❌ | 身份证正面照片URL |
| `urlBack` | `String` | ❌ | 身份证反面照片URL |
| `cardId` | `String` | ❌ | 身份证号 |
| `channel` | `String` | ✅ | 接口调用方 |
| `modifierId` | `Long` | ❌ | 修改人id |
| `modifierName` | `String` | ❌ | 修改人名称 |
| `modifyTime` | `Date` | ❌ | 修改时间 |
| `jobNumber` | `String` | ❌ | 用户工号 |

### 2.3 响应结构

| 项目 | 内容 |
|------|------|
| 统一包装 | `com.dst.steed.common.domain.response.Response` |
| data 类型 | `Object` |
| 说明 | `Modifyjobnumber返回结果` |

### 2.4 Feign Client 定义

```java
@FeignClient(name = "dst-user-core-service", contextId = "FoundationAdminClientApi")
public interface FoundationAdminClientApi {

    @RequestMapping("/foundation/admin/modifyJobNumber")
    Response<Object> modifyJobNumber(@RequestBody ModifyAdminParam query);
}
```

### 2.5 DTO 定义

#### ModifyAdminParam

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `adminId` | `String` | ✅ | 用户ID |
| `realName` | `String` | ❌ | 用户姓名 |
| `urlFront` | `String` | ❌ | 身份证正面照片URL |
| `urlBack` | `String` | ❌ | 身份证反面照片URL |
| `cardId` | `String` | ❌ | 身份证号 |
| `channel` | `String` | ✅ | 接口调用方 |
| `modifierId` | `Long` | ❌ | 修改人id |
| `modifierName` | `String` | ❌ | 修改人名称 |
| `modifyTime` | `Date` | ❌ | 修改时间 |
| `jobNumber` | `String` | ❌ | 用户工号 |

### 2.6 示例

```json
null
```

### 2.7 业务校验规则

无业务错误定义。

### 2.8 源码定位

| 项目 | 内容 |
|------|------|
| 源码文件 | `src/main/java/com/dst/user/core/modules/business/foundation/controller/FoundationAdminController.java` |
| 方法签名 | `modifyJobNumber(ModifyAdminParam param)` |
| 接口 owner | `luohao` |

---

## 3. 记录个人名称变更日志

### 3.1 基本信息

| 项目 | 内容 |
|------|------|
| operationId | `user-center.business.aiAgent.logMessage` |
| 请求方法 | `POST` |
| 请求路径 | `/foundation/admin/logAdminChangeInfo` |
| 简要描述 | `执行Logadminchangeinfo并返回Object` |

### 3.2 请求参数

#### Body 参数

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `oldAdmin` | `Admin` | ❌ | 个人用户旧信息 |
| `newAdmin` | `Admin` | ❌ | 个人用户新信息 |
| `channel` | `String` | ❌ | 渠道 |
| `unifyLogEvent` | `String` | ❌ | 统一日志事件 |

### 3.3 响应结构

| 项目 | 内容 |
|------|------|
| 统一包装 | `com.dst.steed.common.domain.response.Response` |
| data 类型 | `Object` |
| 说明 | `Logadminchangeinfo执行结果` |

### 3.4 Feign Client 定义

```java
@FeignClient(name = "dst-user-core-service", contextId = "FoundationAdminClientApi")
public interface FoundationAdminClientApi {

    @PostMapping("/foundation/admin/logAdminChangeInfo")
    Response<Object> logMessage(@RequestBody AdminLogParam query);
}
```

### 3.5 DTO 定义

#### AdminLogParam

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `oldAdmin` | `Admin` | ❌ | 个人用户旧信息 |
| `newAdmin` | `Admin` | ❌ | 个人用户新信息 |
| `channel` | `String` | ❌ | 渠道 |
| `unifyLogEvent` | `String` | ❌ | 统一日志事件 |

#### Admin

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `creatorId` | `Long` | ❌ |  |
| `creatorName` | `String` | ❌ |  |
| `createTime` | `Date` | ❌ |  |
| `modifierId` | `Long` | ❌ |  |
| `modifierName` | `String` | ❌ |  |
| `modifyTime` | `Date` | ❌ |  |
| `id` | `Long` | ❌ | 主键ID |
| `username` | `String` | ❌ | 帐号 |
| `password` | `String` | ❌ | 密码MD5(密码+盐) |
| `salt` | `String` | ❌ | 盐 |
| `realname` | `String` | ❌ | 姓名 |
| `avatar` | `String` | ❌ | 头像 |
| `phone` | `String` | ❌ | 电话 |
| `phoneEncrypt` | `String` | ❌ |  |
| `phoneMask` | `String` | ❌ |  |
| `email` | `String` | ❌ | 邮箱 |
| `sex` | `Integer` | ❌ | 性别 |
| `ddUserId` | `String` | ❌ | 钉钉用户id |
| `isSync` | `Integer` | ❌ | 钉钉同步状态0未同步1已同步 |
| `locked` | `Integer` | ❌ | 状态(0:正常,1:锁定,2:注销) |
| `ctime` | `Long` | ❌ | 创建时间 |
| `jobNumber` | `String` | ❌ | 用户工号 |
| `roleType` | `Integer` | ❌ |  |
| `userType` | `Integer` | ❌ | 用户类型,1-内部用户;2-外部用户 |
| `nickname` | `String` | ❌ | 昵称 |
| `regInviteCode` | `String` | ❌ | 注册邀请码 |
| `regChannel` | `Integer` | ❌ | 注册渠道(1.地上铁App 2.H5 ) |
| `channelCode` | `String` | ❌ | 渠道code |
| `activityCode` | `String` | ❌ | 活动code |
| `type` | `Integer` | ❌ | 用户类型 1个人用户 2企业用户 |
| `payPassword` | `String` | ❌ | 支付密码 |
| `creatorId` | `Long` | ❌ | 创建人id |
| `creatorName` | `String` | ❌ | 创建人名称 |
| `createTime` | `Date` | ❌ | 创建时间 |
| `modifierId` | `Long` | ❌ | 修改人id |
| `modifierName` | `String` | ❌ | 修改人名称 |
| `modifyTime` | `Date` | ❌ | 修改时间 |
| `employeeId` | `Long` | ❌ | 员工id（OA） |
| `applyLogOffTime` | `Date` | ❌ | 申请注销时间 |
| `marketingStatus` | `Integer` | ❌ | 营销状态(1:常规交易用户 2:灰名单 3:黑名单) |

#### BaseDO

| 字段名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `creatorId` | `Long` | ❌ |  |
| `creatorName` | `String` | ❌ |  |
| `createTime` | `Date` | ❌ |  |
| `modifierId` | `Long` | ❌ |  |
| `modifierName` | `String` | ❌ |  |
| `modifyTime` | `Date` | ❌ |  |

### 3.6 示例

```json
null
```

### 3.7 业务校验规则

无业务错误定义。

### 3.8 源码定位

| 项目 | 内容 |
|------|------|
| 源码文件 | `src/main/java/com/dst/user/core/modules/business/foundation/controller/FoundationAdminController.java` |
| 方法签名 | `logMessage(AdminLogParam param)` |
| 接口 owner | `luohao` |
