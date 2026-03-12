---
domain: "user"
service: "dst-user-core-service"

owner:
  name: "luohao"
  contact: "[optional wecom/email]"

updatedAt: "2026-03-12"
status: "active"

source:
  repo: "/Users/luohao/Desktop/DST/user-center/dst-user-core-service"
  defaultBranch: "main"

frameworkProfile: "dst-steed-java-openfeign"

feign:
  target:
    type: "service-name"
    value: "dst-user-core-service"
  pathPrefix: ""
  contextIdPrefix: ""

pathRules:
  controllerBasePathStyle: "explicit-controller-mapping"
  notes:
    - "innerapi controller"

generationNotes:
  - "Java consumer 默认生成 OpenFeign client。"
troubleshootingNotes:
  - "统一返回使用 Response<T>。"
---

# dst-user-core-service 服务信息

## 基本信息

- 域：`user`
- 服务名：`dst-user-core-service`
- 状态：`active`
- 项目 owner：`luohao`
- 联系方式：`[optional wecom/email]`
- 最近更新时间：`2026-03-12`

## 仓库信息

- 仓库地址：`/Users/luohao/Desktop/DST/user-center/dst-user-core-service`
- 默认分支：`main`

## 框架约定

- 框架配置：`dst-steed-java-openfeign`
- 统一返回：`Response<T>`（公司默认）
- 鉴权处理：公司统一框架处理

## Feign 生成约定

- Feign 目标类型：`service-name`
- Feign 目标值：`dst-user-core-service`
- 默认 path 前缀：``
- contextId 前缀：``

## 路径规则说明

- Controller 路径策略：`explicit-controller-mapping`
- 备注：
  - `innerapi controller`

## 生成备注

- `Java consumer 默认生成 OpenFeign client。`

## 排障备注

- `统一返回使用 Response<T>。`
