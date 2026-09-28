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

## 本机已完成

- 已生成全部项目文件和配置模板。
- 已建立 `backend/.venv` Python 3.12 虚拟环境。
- 已安装后端基础依赖：FastAPI、Uvicorn、SQLAlchemy、PyMySQL、Redis、JWT、pytest、ruff。
- 已安装管理端 npm 依赖并生成 `admin-web/package-lock.json`。
- 已生成后端 `.env` 本地开发配置（仅占位值，不可用于生产）。

## 启动顺序（当前电脑可直接使用的本地模式）

1. 双击或在 PowerShell 执行：`scripts\start_backend.ps1`（SQLite、本地文件存储、mock 存证，不依赖 Docker）。
2. 另开 PowerShell 执行：`scripts\start_admin.ps1`。
3. 后端文档：`http://127.0.0.1:8000/docs`；管理端：`http://127.0.0.1:5173`。
4. 微信小程序：使用微信开发者工具打开 `miniprogram`，将接口地址配置为 `http://127.0.0.1:8000/api`。

## 生产/容器模式

安装 Docker Desktop 并启动 Docker Engine 后，在本目录执行：`docker compose -f infra/docker-compose.yml up -d mysql redis minio`。然后将 `backend/.env` 的数据库、Redis 和对象存储配置改回容器地址；区块链仍需配置真实 BaaS 凭证。

## 账号和密钥说明

`.env.example` 和 `infra/.env.example` 只包含本地开发占位值。真实微信 AppID、云服务器、OSS、BaaS、JWT 密钥不得提交到公共仓库。
