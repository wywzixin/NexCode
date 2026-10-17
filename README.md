# NexCode

基于 Python 的终端 AI 编程助手，支持 Anthropic、OpenAI 和兼容 OpenAI 的模型服务。

## 功能

- 终端交互界面与命令行非交互运行。
- 文件读写、代码搜索、命令执行和权限控制。
- MCP 工具、Skills、子 Agent 与多 Agent 协作。
- 会话管理、上下文压缩、项目记忆和 Git worktree。
- 通过 `--remote` 启动浏览器界面。

## 安装

需要 Python 3.11 或更高版本，以及 [uv](https://docs.astral.sh/uv/)。使用通过 `npx` 启动的 MCP 服务时，还需要 Node.js。

```bash
git clone https://github.com/wywzixin/NexCode.git
cd NexCode
uv sync --dev
```

## 配置

将根目录的 `config.yaml.example` 复制到 `.nexcode/config.yaml`，按所用服务修改 `protocol`、`base_url` 和 `model`。

Windows PowerShell：

```powershell
New-Item -ItemType Directory -Force .nexcode | Out-Null
Copy-Item config.yaml.example .nexcode/config.yaml
$env:ANTHROPIC_API_KEY = "YOUR_API_KEY"
uv run nexcode
```

macOS / Linux：

```bash
mkdir -p .nexcode
cp config.yaml.example .nexcode/config.yaml
export ANTHROPIC_API_KEY="YOUR_API_KEY"
uv run nexcode
```

使用 OpenAI 或兼容服务时，将环境变量改为 `OPENAI_API_KEY`，并在配置中选择对应的 provider。`api_key` 留空时，程序会读取环境变量。本地 `.nexcode/` 和 `.env` 文件已加入 Git 忽略规则。

## 使用

```bash
uv run nexcode --help
uv run nexcode -p "介绍当前项目的目录结构"
uv run nexcode -p "检查当前项目" --output-format stream-json
uv run nexcode --remote
```

## 测试

```bash
uv run pytest
```
