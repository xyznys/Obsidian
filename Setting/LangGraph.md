
##### why LangGraph
1. 用 Agent（[[Claude Code]]) 去构建 Agent（[[LangGraph]]）
2. 80% 用 [[LangGraph]] + 20% 原生代码 [[Python]]
	LangGraph：控制流程 + Python / JS：写工具函数（Excel / API / DB）
	原生代码解决“能不能做” + LangGraph 解决“能不能长期做”

##### 前置条件
1. [[Python]] 3.10+
2. pip
3. LLM
	1. 本地 [[Ollama]]
	2. OpenAI / Claude API

##### 安装 LangGraph
1. 使用本地 ollama 模型
	1. `pip install langgraph langchain ollama`
2. 确保 ollama 在后台运行中
	1. `curl http://localhost:11434`
3. 安装依赖
	1. `pip install langgraph langchain langchain-community ollama`

##### 代码结构 - 本地python项目
新建文件夹
	langgraph-agent-demo/
	├── app.py              ← 主程序（你运行的入口）
	├── nodes.py           ← 各个LLM节点函数
	├── state.py           ← 状态定义
	├── requirements.txt   ← 依赖
	└── .env               ← 可选（模型/配置）

##### 运行
	1. 进入项目目录
	2. 运行 app.py

