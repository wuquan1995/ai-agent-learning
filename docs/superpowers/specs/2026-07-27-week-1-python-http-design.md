# 第 1 周：Python、HTTP 与密钥边界设计

## 目标

用 Python 3.12 与 uv 建立本项目统一开发环境，并实现一个不依赖 LLM SDK 的 HTTP/JSON 客户端。该客户端能从环境变量读取 token，清晰区分成功、超时、认证失败和服务端失败，并由自动化测试覆盖。

## 原则

1. 先理解 HTTP 请求、JSON、超时与异常边界，再接入任何模型 SDK。
2. token 只能从环境变量读取；不得写入源代码、测试输出、日志或 Git。
3. 运行时代码与 HTTP 传输细节分层，便于下一周接入真实模型接口。
4. 所有新增学习文档和代码注释使用中文。

## 技术选择

- Python：3.12。
- 环境和依赖管理：uv。
- HTTP：`httpx`，使用显式超时。
- 测试：pytest + respx，拦截 HTTP 请求而不访问真实网络。
- 包布局：`src/` layout，避免从当前目录意外导入未安装代码。

## 文件边界

- `pyproject.toml`：Python 版本、运行依赖、开发依赖与 pytest 配置。
- `src/agent_learning/config.py`：定义 `Settings`，只负责读取和校验 `AGENT_LEARNING_API_TOKEN`。
- `src/agent_learning/http_client.py`：定义 `ApiClient`、`ApiResponse` 和受控异常；负责请求、JSON 解码和错误映射。
- `src/agent_learning/cli.py`：提供最小命令行入口，用演示地址发起请求并输出安全的结果摘要。
- `tests/test_config.py`：验证缺失 token 与有效 token 的配置行为。
- `tests/test_http_client.py`：验证 2xx JSON、超时、401 和 5xx 映射。
- `.gitignore`：忽略 `.venv/`、`.env`、Python 缓存和覆盖率文件。
- `docs/week-01.md`：中文运行说明、学习问题与复盘模板。

## 数据流

命令行入口创建 `Settings`，读取环境变量 token 并传给 `ApiClient`。客户端将 token 放入 Authorization 请求头、发送 JSON 请求并返回 `ApiResponse`；网络、认证、服务端和解码错误转换为不同的异常类型。日志和命令行输出只显示状态、请求 ID 与耗时，不显示 token。

## 验收标准

1. `uv run pytest` 通过配置与四类 HTTP 行为测试。
2. 缺失 token 时程序以中文错误提示退出，且不发起网络请求。
3. 401、5xx、超时均可由调用方区分。
4. `rg "AGENT_LEARNING_API_TOKEN" -g '!*.md'` 只匹配配置读取和测试，不出现真实密钥。
5. `docs/week-01.md` 可让另一位开发者在不依赖本机隐式状态的情况下完成环境初始化与测试。
