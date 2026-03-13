# FoundationAdminController 接口文档

## Controller 概览

- service: `dst-user-core-service`
- domain: `user-center`
- basePath: `/foundation/admin`

## 方法摘要

- `user-center.innerapi.aiAgent.getAdminInformation` 获取个人用户信息(统一入口)
- `user-center.innerapi.aiAgent.modifyAdminInformation` 修改个人用户信息(统一入口)
- `user-center.innerapi.aiAgent.modifyJobNumber` 根据用户ID修改个人用户工号
- `user-center.innerapi.aiAgent.logMessage` 记录个人名称变更日志

## 1. 获取个人用户信息(统一入口)

### 基本信息

- operationId: `user-center.innerapi.aiAgent.getAdminInformation`
- method: `REQUEST`
- path: `/foundation/admin/getAdminInformation`
- description: 处理Getadmininformation并返回结果

### 请求

#### body

- type: `QueryAdminParam`
- required: `true`
- description: getAdminInformation 请求体

### 响应

- envelopeType: `Response`
- dataType: `List<AdminInformationVO>`
- description: Getadmininformation返回结果

### DTO 摘要

#### Request Types

- `QueryAdminParam`
  - `adminIds` `List<String>` optional 个人用户id集合
#### Response Types

- `AdminInformationVO`
  - `id` `String` optional 个人用户id
  - `regChannel` `Integer` optional 注册渠道: 1.地上铁App 2.H5
  - `phone` `String` optional 手机号
  - `phoneMask` `String` optional
  - `realname` `String` optional 姓名
  - `urlFront` `String` optional 身份证正面
  - `urlBack` `String` optional 身份证反面
  - `cardId` `String` optional 身份证号
  - `reviewsStatus` `Integer` optional 认证状态: 1 认证中 2 已驳回 3 已认证 4未认证 5已过期
  - `modifierId` `Long` optional 修改人id
  - `modifierName` `String` optional 修改人名称

### 错误信息

- 无

### 源码定位

- className: `FoundationAdminController`
- methodName: `getAdminInformation`
- signature: `getAdminInformation(QueryAdminParam param)`

## 2. 修改个人用户信息(统一入口)

### 基本信息

- operationId: `user-center.innerapi.aiAgent.modifyAdminInformation`
- method: `REQUEST`
- path: `/foundation/admin/modifyAdminInformation`
- description: 处理Modifyadmininformation并返回结果

### 请求

#### body

- type: `ModifyAdminParam`
- required: `true`
- description: modifyAdminInformation 请求体

### 响应

- envelopeType: `Response`
- dataType: `Object`
- description: Modifyadmininformation返回结果

### DTO 摘要

#### Request Types

- `ModifyAdminParam`
  - `adminId` `String` required 用户ID constraints=@NotEmpty
  - `realName` `String` optional 用户姓名
  - `urlFront` `String` optional 身份证正面照片URL
  - `urlBack` `String` optional 身份证反面照片URL
  - `cardId` `String` optional 身份证号
  - `channel` `String` required 接口调用方 constraints=@NotEmpty
  - `modifierId` `Long` optional 修改人id
  - `modifierName` `String` optional 修改人名称
  - `modifyTime` `Date` optional 修改时间
  - `jobNumber` `String` optional 用户工号
#### Response Types

- 无

### 错误信息

- 无

### 源码定位

- className: `FoundationAdminController`
- methodName: `modifyAdminInformation`
- signature: `modifyAdminInformation(ModifyAdminParam param)`

## 3. 根据用户ID修改个人用户工号

### 基本信息

- operationId: `user-center.innerapi.aiAgent.modifyJobNumber`
- method: `REQUEST`
- path: `/foundation/admin/modifyJobNumber`
- description: 处理Modifyjobnumber并返回结果

### 请求

#### body

- type: `ModifyAdminParam`
- required: `true`
- description: modifyJobNumber 请求体

### 响应

- envelopeType: `Response`
- dataType: `Object`
- description: Modifyjobnumber返回结果

### DTO 摘要

#### Request Types

- `ModifyAdminParam`
  - `adminId` `String` required 用户ID constraints=@NotEmpty
  - `realName` `String` optional 用户姓名
  - `urlFront` `String` optional 身份证正面照片URL
  - `urlBack` `String` optional 身份证反面照片URL
  - `cardId` `String` optional 身份证号
  - `channel` `String` required 接口调用方 constraints=@NotEmpty
  - `modifierId` `Long` optional 修改人id
  - `modifierName` `String` optional 修改人名称
  - `modifyTime` `Date` optional 修改时间
  - `jobNumber` `String` optional 用户工号
#### Response Types

- 无

### 错误信息

- 无

### 源码定位

- className: `FoundationAdminController`
- methodName: `modifyJobNumber`
- signature: `modifyJobNumber(ModifyAdminParam param)`

## 4. 记录个人名称变更日志

### 基本信息

- operationId: `user-center.innerapi.aiAgent.logMessage`
- method: `POST`
- path: `/foundation/admin/logAdminChangeInfo`
- description: 处理Logadminchangeinfo并返回结果

### 请求

#### body

- type: `AdminLogParam`
- required: `true`
- description: logMessage 请求体

### 响应

- envelopeType: `Response`
- dataType: `Object`
- description: Logadminchangeinfo返回结果

### DTO 摘要

#### Request Types

- `AdminLogParam`
  - `oldAdmin` `Admin` optional 个人用户旧信息
  - `newAdmin` `Admin` optional 个人用户新信息
  - `channel` `String` optional 渠道
  - `unifyLogEvent` `String` optional 统一日志事件
#### Response Types

- 无

### 错误信息

- 无

### 源码定位

- className: `FoundationAdminController`
- methodName: `logMessage`
- signature: `logMessage(AdminLogParam param)`
