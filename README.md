# 校园电子废弃物回收追踪系统 · 所需资源

本目录根据《校园电子废弃物回收追踪系统--需求文档》预先搭建，包含后端 API、管理端、小程序端、数据库脚本、Docker 基础设施和联调文档。

## 已按需求准备的技术边界

- 用户端：微信小程序（扫码、GPS、回收记录、去向追溯）
- 管理端：React + Vite + TypeScript（后勤/环保部门）
- 后端：FastAPI + SQLAlchemy + JWT 预留
- 数据库：MySQL 8.0
- 缓存：Redis
- 文件/照片：MinIO（本地模拟云 OSS，生产环境可替换为阿里云 OSS/腾讯云 COS）
- 区块链：可插拔存证适配器，默认 `mock`，预留蚂蚁链/至信链 BaaS 配置
- 部署：Docker Compose

## 目录

```text
backend/       FastAPI 后端骨架、数据模型、健康检查、核心 API
admin-web/     React + Vite 管理端骨架
miniprogram/   微信小程序原生项目骨架（需用微信开发者工具打开）
infra/         Docker Compose、MySQL 初始化脚本、环境变量示例
docs/          环境说明、接口清单、联调说明
scripts/       Windows 启停和环境检查脚本
```
