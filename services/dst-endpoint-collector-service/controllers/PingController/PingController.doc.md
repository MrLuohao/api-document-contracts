# PingController 接口文档

## Controller 概览

- service: `dst-endpoint-collector-service`
- domain: `analytics`
- basePath: ``

## 方法摘要

- `analytics.innerapi.aiAgent.ping` 系统心跳默认接口

## 1. 系统心跳默认接口

### 基本信息

- operationId: `analytics.innerapi.aiAgent.ping`
- method: `GET`
- path: `/ping`
- description: 处理Ping并返回结果

### 请求

- 无请求参数

### 响应

- envelopeType: `Response`
- dataType: `String`
- description: Ping返回结果

### DTO 摘要

#### Request Types

- 无
#### Response Types

- 无

### 错误信息

- 无

### 源码定位

- className: `PingController`
- methodName: `ping`
- signature: `ping()`
