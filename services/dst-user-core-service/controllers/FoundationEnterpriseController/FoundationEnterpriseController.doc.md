# FoundationEnterpriseController 接口文档

## Controller 概览

- service: `dst-user-core-service`
- domain: `user-center`
- basePath: `/foundation/enterprise`

## 方法摘要

- `user-center.innerapi.aiAgent.getEnterpriseInformation` 获取企业用户信息(统一入口)
- `user-center.innerapi.aiAgent.modifyEnterpriseInformation` 修改企业用户信息(统一入口)
- `user-center.innerapi.aiAgent.foundationEnterprise.logMessage` 记录企业名称变更日志

## 1. 获取企业用户信息(统一入口)

### 基本信息

- operationId: `user-center.innerapi.aiAgent.getEnterpriseInformation`
- method: `REQUEST`
- path: `/foundation/enterprise/getEnterpriseInformation`
- description: 处理Getenterpriseinformation并返回结果

### 请求

#### body

- type: `QueryEnterpriseParam`
- required: `true`
- description: getEnterpriseInformation 请求体

### 响应

- envelopeType: `Response`
- dataType: `List<EnterpriseInformationVO>`
- description: Getenterpriseinformation返回结果

### DTO 摘要

#### Request Types

- `QueryEnterpriseParam`
  - `enterpriseIds` `List<String>` optional 企业用户id集合
#### Response Types

- `EnterpriseInformationVO`
  - `id` `String` optional 企业用户id
  - `dataChannel` `String` optional 数据渠道
  - `businessStatus` `String` optional 企业用户状态 （存续、吊销）
  - `enterpriseCreditCode` `String` optional 企业信用代码
  - `enterpriseName` `String` optional 企业名称
  - `enterpriseLegalName` `String` optional 法人姓名
  - `enterpriseRegister` `String` optional 注册资本
  - `enterpriseModel` `String` optional 工商类型
  - `enterpriseResidence` `String` optional 住所
  - `enterpriseRegisterDate` `Date` optional 成立日期
  - `enterpriseBusinessDate` `String` optional 营业期限
  - `enterpriseBusinessScope` `String` optional 经营范围
  - `enterpriseLicense` `String` optional 营业执照
  - `enterpriseCertificate` `String` optional 证明函
  - `enterpriseStatus` `Integer` optional 认证状态
  - `legalName` `String` optional 经办人姓名
  - `legalCardId` `String` optional 经办人身份证号
  - `legalPhone` `String` optional 经办人手机号
  - `legalPhoneMask` `String` optional
  - `legalUrlFront` `String` optional 经办人身份证正面
  - `legalUrlBack` `String` optional 经办人身份证反面
  - `modifierId` `Long` optional 修改人id
  - `modifierName` `String` optional 修改人名称

### 错误信息

- 无

### 源码定位

- className: `FoundationEnterpriseController`
- methodName: `getEnterpriseInformation`
- signature: `getEnterpriseInformation(QueryEnterpriseParam param)`

## 2. 修改企业用户信息(统一入口)

### 基本信息

- operationId: `user-center.innerapi.aiAgent.modifyEnterpriseInformation`
- method: `REQUEST`
- path: `/foundation/enterprise/modifyEnterpriseInformation`
- description: 处理Modifyenterpriseinformation并返回结果

### 请求

#### body

- type: `ModifyEnterpriseParam`
- required: `true`
- description: modifyEnterpriseInformation 请求体

### 响应

- envelopeType: `Response`
- dataType: `Object`
- description: Modifyenterpriseinformation返回结果

### DTO 摘要

#### Request Types

- `ModifyEnterpriseParam`
  - `enterpriseId` `String` required 企业用户ID constraints=@NotEmpty
  - `enterpriseCreditCode` `String` optional 企业信用代码
  - `enterpriseName` `String` optional 企业名称
  - `enterpriseLegalName` `String` optional 法人代表
  - `enterpriseRegister` `String` optional 注册资本
  - `enterpriseModel` `String` optional 工商类型
  - `enterpriseResidence` `String` optional 住所
  - `enterpriseRegisterDate` `Date` optional 成立日期 constraints=@JsonFormat
  - `enterpriseBusinessDate` `String` optional 营业期限 constraints=@JsonFormat
  - `enterpriseBusinessScope` `String` optional 经营范围
  - `enterpriseLicense` `String` optional 企业营业执照图片
  - `enterpriseCertificate` `String` optional 证明函
  - `channel` `String` required 接口调用方 constraints=@NotEmpty
  - `modifierId` `Long` optional 修改人id
  - `modifierName` `String` optional 修改人名称
  - `modifyTime` `Date` optional 修改时间
#### Response Types

- 无

### 错误信息

- 无

### 源码定位

- className: `FoundationEnterpriseController`
- methodName: `modifyEnterpriseInformation`
- signature: `modifyEnterpriseInformation(ModifyEnterpriseParam param)`

## 3. 记录企业名称变更日志

### 基本信息

- operationId: `user-center.innerapi.aiAgent.foundationEnterprise.logMessage`
- method: `POST`
- path: `/foundation/enterprise/logEnterpriseChangeInfo`
- description: 处理Logenterprisechangeinfo并返回结果

### 请求

#### body

- type: `EnterpriseLogParam`
- required: `true`
- description: logMessage 请求体

### 响应

- envelopeType: `Response`
- dataType: `Object`
- description: Logenterprisechangeinfo返回结果

### DTO 摘要

#### Request Types

- `EnterpriseLogParam`
  - `oldEnterprise` `UserEnterprise` optional
  - `newEnterprise` `UserEnterprise` optional
  - `channel` `String` optional
  - `type` `int` optional
#### Response Types

- 无

### 错误信息

- 无

### 源码定位

- className: `FoundationEnterpriseController`
- methodName: `logMessage`
- signature: `logMessage(EnterpriseLogParam param)`
