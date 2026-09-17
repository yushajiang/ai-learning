# AI 起点

一个面向零基础学习者的 AI 学习网站。用时间线、生活化案例和可操作的演示，理解大语言模型、本地部署与提示词工程。

![AI 起点首页](docs/images/home.png)

## 学习内容

| 页面 | 内容 |
| --- | --- |
| AI 编年史 | 1956—2026 年的 17 个代表节点，介绍 Transformer、RAG、长上下文、LangChain、LangGraph、Agent、Skills 和 Harness |
| 第一课：大语言模型 | 上下文预测实验、流式生成演示、注意力示意，以及模型参数、上下文和 RAG 的区别 |
| 第二课：本地部署 | 使用 Ollama 运行 Qwen3 0.6B，提供命令复制、PowerShell API 示例和常见问题排查 |
| 第三课：提示词工程 | 发展脉络、四种实战配方、角色卡、提示词注入对照和实时提示词编辑 |

![AI 编年史](docs/images/history.png)

## 交互与设计

- 大字排版、留白、渐变视觉和细线时间轴，兼容桌面与手机。
- 流式演示支持暂停、继续、重置和速度调整。
- 切换上下文，观察候选内容变化；切换角色，比较表达方式。
- 对比提示词注入的失败情形与期望防御行为。
- 同源页面提前加载，并在页面内切换，保留独立 URL、浏览器返回及无 JavaScript 时的正常链接导航。
- 提供官方资料链接，并嵌入 Hugging Face 官方课程视频。

![流式生成教学演示](docs/images/streaming.png)

![角色卡示例](docs/images/roles.png)

## 本地运行

项目使用原生 HTML、CSS 和 JavaScript，没有构建步骤或 npm 依赖。

安装 Python 后，在仓库目录运行：

```bash
python -m http.server 4173 --directory dist --bind 127.0.0.1
```

打开 <http://127.0.0.1:4173/>。请通过 HTTP 服务访问，避免直接以 `file://` 打开导致预加载受到限制。

## 目录结构

```text
dist/
├── index.html              # 首页
├── history/index.html      # AI 编年史
├── lessons/
│   ├── llm/index.html       # 大语言模型
│   ├── local/index.html     # 本地部署
│   └── prompt/index.html    # 提示词工程
├── learning.js             # 课程交互与快速导航
├── style.css               # 基础样式
├── course.css              # 课程样式
├── lab.css                 # 交互实验样式
└── history.css             # 编年史样式
docs/images/                # README 页面截图
```

`dist/` 可交给支持静态 HTML 的服务器托管。站内链接从根路径开始，部署时应把 `dist/` 设置为站点根目录；子路径托管需要调整链接。

`.openai/hosting.json` 是现有 Sites 托管配置，本地运行不依赖它。`.sites-runtime/` 为本地临时工作文件，不进入仓库。

## 演示边界

交互中的候选概率、流式回答、角色回答与注入对照均为预设教学模拟，没有调用在线模型。提示词和命令可以复制到实际模型中实验；真实输出因模型、设置和输入而异。

角色提示词可以在部分行为、语气和格式任务中减少微调需求，但不会更新模型参数，也不能完全替代微调。提示词分隔符不构成完整的注入防御，实际系统仍需权限控制、输出校验与持续测试。

视频来自 YouTube，播放取决于网络可达性。网页未加入 Apple 品牌素材，视觉设计受到其产品页面风格启发。

## 参考资料

- [Hugging Face：什么是 LLM](https://huggingface.co/learn/agents-course/en/unit1/what-are-llms)
- [Ollama 快速入门](https://docs.ollama.com/quickstart)
- [Qwen3 0.6B](https://ollama.com/library/qwen3:0.6b)
- [SillyTavern 角色设计](https://docs.sillytavern.app/usage/core-concepts/characterdesign/)
- [DSPy](https://github.com/stanfordnlp/dspy)
- [LangGraph 介绍](https://www.langchain.com/blog/langgraph)
- [Anthropic：上下文工程](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
- [Anthropic：提示词注入防御](https://www.anthropic.com/research/prompt-injection-defenses)

更多论文和官方公告保留在对应课程与编年史节点中。网站内容核验于 2026 年 9 月；外部文档与工具可能继续更新。
