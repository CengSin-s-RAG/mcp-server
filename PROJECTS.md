# 项目索引

## mcp-server

路径：`/Users/cengsin/my_projects/mcp-server`

### 概述
这是一个基于 **MCP (Model Context Protocol)** 协议实现的工具服务器，名为 `rag_finance_news_tools`。它为 AI 模型提供金融新闻相关的 RAG（检索增强生成）工具支持。

### 技术栈
- **语言**: Go
- **协议**: MCP (Model Context Protocol)
- **数据库**: 
  - MySQL (基础数据)
  - Qdrant (向量检索)
- **存储**: MinIO
- **AI/LLM**: OpenAI (通过 client 初始化)
- **Temporal**: 工作流，本地启动脚本路径(~/GolandWorkSapce2025/money-transfer-project-template-go)

### 主要功能
- 提供 Streamable HTTP Server 运行在 `:8085` 端口。
- 注册了一系列金融新闻检索工具（见 `tools/` 目录）。
- 支持向量检索和元数据查询。

### 项目结构
```
├── ai/             # AI 相关逻辑
├── client/         # 各种客户端初始化 (MySQL, Qdrant, OpenAI, MinIO)
├── config/         # 配置解析
├── dao/            # 数据访问层
├── tools/          # MCP 工具注册与实现
├── util/           # 公共工具类
└── main.go         # 入口文件，启动 HTTP MCP 服务
```

### 分支说明
- **`main`**: 主分支，包含核心 MCP 服务实现。

### 依赖关系
- **被调用者**: 被 Clawdbot 或其他支持 MCP 的客户端（如 Claude Desktop, Cursor）调用。
- **外部服务**: 依赖 MySQL, Qdrant, MinIO 以及 OpenAI API。

### 启动说明
1. 确保相关数据库服务（MySQL, Qdrant）已启动。
2. 检查 `config/` 下的配置文件。
3. 运行 `go run main.go`。
   - 服务默认在 `http://localhost:8085` 暴露 MCP 接口。
