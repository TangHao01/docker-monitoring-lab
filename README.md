# Docker 单机 Web 服务与监控平台

本项目通过 Docker 和 Docker Compose，在单台主机上实现自定义 Web 服务的部署与 Prometheus/Grafana 监控体系。

## 技术栈
- **容器化**：Docker, Dockerfile
- **编排**：Docker Compose
- **监控与可视化**：Prometheus, Grafana, Node Exporter

## 文件说明
- `index.html`：自定义的网页文件。
- `Dockerfile`：用于构建自定义 Nginx 镜像。
- `prometheus.yml`：Prometheus 监控抓取配置。
- `docker-compose.yml`：用于一键拉起监控全家桶。

## 避坑指南
在搭建过程中遇到并解决了以下问题：
1. **Grafana 导入报错**：解决新版 Grafana (Schema v2) 导入旧版模板时 `Invalid or unknown dashboard schema` 的兼容性问题（通过直接上传 JSON 文件解决）。
2. **跨平台乱码**：Windows 环境下编辑的 HTML 文件在 Linux 容器内显示乱码，通过在 HTML 中声明 `<meta charset="UTF-8">` 解决。
3. **Docker 引擎报错**：遇到 `500 Internal Server Error`，通过重启 WSL 及重置 Docker Desktop 引擎排查修复。
