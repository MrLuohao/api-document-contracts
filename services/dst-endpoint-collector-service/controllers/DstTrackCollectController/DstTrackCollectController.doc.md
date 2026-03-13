# DstTrackCollectController 接口文档

## Controller 概览

- service: `dst-endpoint-collector-service`
- domain: `analytics`
- basePath: `/api/v1/track`

## 方法摘要

- `analytics.innerapi.aiAgent.collect` 埋点数据上报接口

## 1. 埋点数据上报接口

### 基本信息

- operationId: `analytics.innerapi.aiAgent.collect`
- method: `POST`
- path: `/api/v1/track`
- description: 处理DstTrackCollect并返回结果

### 请求

#### body

- type: `DstTrackCollectDTO`
- required: `true`
- description: collect 请求体

### 响应

- envelopeType: `Response`
- dataType: `Boolean`
- description: Boolean返回结果

### DTO 摘要

#### Request Types

- `DstTrackCollectDTO`
  - `appId` `String` required 应用标识，用于区分不同应用 constraints=@NotBlank
  - `appName` `String` optional 应用名称
  - `uid` `String` optional 用户唯一标识
  - `event` `String` required 事件名称，采用下划线命名 constraints=@NotBlank
  - `pagePath` `String` required 页面路径 constraints=@NotBlank
  - `time` `Long` required 客户端时间戳（毫秒） constraints=@NotNull,@Min
  - `platform` `String` optional 平台标识
  - `device` `String` optional 设备型号
  - `sessionId` `String` optional 会话ID，用于追踪单次访问 constraints=@Size
  - `pageTitle` `String` optional 页面标题 constraints=@Size
  - `properties` `Map<String,Object>` optional 自定义事件属性
#### Response Types

- 无

### 错误信息

- 无

### 源码定位

- className: `DstTrackCollectController`
- methodName: `collect`
- signature: `collect(DstTrackCollectDTO collectDTO, HttpServletRequest request)`
