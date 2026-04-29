##### 验证
`ollama --version`
`ollama --help`
`ollama run --help`
`curl http://localhost:11434`
	检查本机（localhost）上运行的 Ollama 服务是否启动、可用并且正在正常监听 11434 端口
	`11434`: 这是一个端口号。网络服务通过端口号来区分不同的应用程序。`11434` 是 Ollama 服务的默认监听端口
	ollama is running 
		这表示 Ollama 状态健康，一切正常
	curl: (7) Failed to connect to localhost port 11434 after 0 ms: Connection refused 
		 你的电脑上没有程序在监听 11434 端口。Ollama 服务没有启动，或者没有正确安装。

##### 免费用户限制
![[Pasted image 20260423144029.png]]


#### 模型
##### 加载模型
`ollama pull qwen3-coder:480b-cloud`
##### 查看全部加载模型
`ollama list`
##### 删除本地模型
`ollama rm gemma3:1b`
##### 复制模型 基于一个现有模型创建一个新名称的副本（通常用于创建自定义模型的基础）
`ollama cp llama3 my-llama3-copy`
##### 查看模型细节
`ollama show qwen3-coder:480b-cloud`
##### 创建自定义模型
1. 创建`Modelfile`文件，将所有的信息，写入，保存。
2. ollama create <我的自定义模型名> -f <Modelfile路径>
	1. `ollama create Model_CompareURL -f C:/Users/Monroe_meng/Documents/Ollama/Model_customized/Modelfile_CompareURL`
	2. 注意文件路径正斜杠
	3. 如果使用相对路径：使用 `./` 表示当前目录， `../` 表示上一级目录。
3. 正常启动模型，输入要求的input类型，就会返回正确的output
	1. 一次性调用
		`ollama run Model_CompareURL {"url1": "https://www.ibm.com/products","url2": "https://www.google.com/search?q=ai"}`
	2. 对话启动
		`ollama run Model_CompareURL`
		输入：`{"url1": "https://www.ibm.com/products","url2": "https://www.google.com/search?q=ai"}`

#### 对话
单词对话 - 直接输入一段提示词，模型生成回答后立即退出
	`ollama run mistral "请用一句话解释量子计算"`

运行/对话（最常用） 启动一个与模型的交互式对话会话。
	`ollama run gemma3:1b`
	你可以持续输入问题，模型会持续回答。
	按 `Ctrl+D` 退出

##### 运行 [[Claude Code]]
`ollama launch claude --model qwen3-coder:480b-cloud`
