# AI Agent Learning（Node.js）

这是一个用 **Node.js、TypeScript、LangChain 与 DeepSeek** 学习 AI Agent 的实践项目。当前示例实现了一个可调用本地天气工具的 Agent，并支持在终端流式输出回答。

## 技术栈

- Node.js 22+
- TypeScript
- LangChain / LangGraph
- Zod（工具参数校验）
- DeepSeek OpenAI 兼容 API

## 已完成内容

- 使用 `createAgent` 组合模型与工具。
- 使用 `tool()` 与 Zod 定义天气查询工具。
- 通过 `ChatOpenAI` 客户端接入 DeepSeek 的 OpenAI 兼容接口。
- 使用 `agent.stream()` 在终端流式显示模型输出。
- 记录常见启动、URL、模型名、额度和 TypeScript 报错的排查过程。

详细学习记录见：[课程笔记](./课程笔记.md)。

## 快速开始

### 1. 安装依赖

```bash
pnpm install
```

### 2. 配置环境变量

在项目根目录创建 `.env`：

```env
DEEPSEEK_API_KEY=你的_DeepSeek_API_Key
DEEPSEEK_API_URL=https://api.deepseek.com

# 可选：LangSmith 调试追踪
# LANGSMITH_TRACING=false
# LANGSMITH_API_KEY=你的_LangSmith_API_Key
# LANGSMITH_PROJECT=ai-agent-learning
```

> 不要提交 `.env`，也不要把 API Key 写入代码或 README。

### 3. 运行项目

```bash
pnpm dev
```

### 4. 类型检查与构建

```bash
pnpm build
```

## 项目结构

```text
.
├── src/
│   └── index.ts       # Agent、工具与流式调用入口
├── 课程笔记.md         # 本次学习笔记
├── package.json       # 脚本和依赖
└── tsconfig.json      # TypeScript 配置
```

## 核心流程

```text
用户问题
  → LangChain Agent
  → DeepSeek 模型判断是否调用工具
  → get_weather 工具返回数据
  → 模型组织自然语言回答
  → 终端流式输出
```

## 下一步练习

1. 将静态天气文本替换为真实天气 API。
2. 为工具调用和网络错误增加异常处理。
3. 添加自动化测试，覆盖工具参数与流式文本格式化。
4. 使用 LangGraph 实现带状态、可恢复的多步骤 Agent 工作流。
