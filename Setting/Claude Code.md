
##### 安装前置要求：
1. [[Node.js]] 18+，完成后验证：
	1. `node -v`
	2. `npm -v`
2. git-bash [[Git]]
	1. Claude Code 需要找到 `bash.exe`，但它在系统的 PATH 环境变量里没找到。你需要手动设置一个环境变量 `CLAUDE_CODE_GIT_BASH_PATH` 来告诉 Claude Code `bash.exe` 的具体位置
	2. git.exe: 这是 Git 版本控制系统的核心命令行程序。当你执行 `git commit`, `git push` 等命令时，实际调用的就是这个可执行文件。它通常位于 `Git\cmd\` 目录下（如 `C:\Program Files\Git\cmd\git.exe`）。
	3. bash.exe: 这是 Git for Windows 打包的 MSYS2 环境中的 Bash shell。它是一个 Unix-style 的命令行环境，提供了你在 Git Bash 中使用的所有 shell 功能（如 `ls`, `cat`, `grep` 等命令）。它通常位于 `Git\bin\` 目录下（如 `C:\Program Files\Git\bin\bash.exe`）

##### 安装
1. NPM 方式 需要先安装 Node.js
2. 一键安装方式（curl/PowerShell）已经将所有的依赖项都打包好了，就不需要额外安装了

3. macOS / Linux / WSL: 
	`curl -fsSL https://claude.ai/install.sh | bash`
4. Windows (PowerShell)
	`irm https://claude.ai/install.ps1 | iex`
	`npm install -g @anthropic-ai/claude-cli`
		如果npm安装失败，备选方案：
		`npx @anthropic-ai/claude-cli "explain this code"`
	`curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd`

##### 设置

###### Git Bash:
setx CLAUDE_CODE_GIT_BASH_PATH "C:\Users\Monroe_meng\AppData\Local\Programs\Git\bin\bash.exe"
###### Login:
set ANTHROPIC_AUTH_TOKEN=ollama
set ANTHROPIC_API_KEY=ollama
set ANTHROPIC_BASE_URL=http://localhost:11434
###### Model
claude --model qwen3-coder:480b-cloud
##### 外接 Ollama 模型
###### 前提
1. [[Ollama]] v0.14 已内置 Anthropic API 兼容层
2. 确保 ollama 在后台运行
###### 设置 Claude Code 接入 Ollama 模型 - 指定 provider
	claude --provider ollama --model llama3
###### 直接写配置文件
	配置写到 C:\Users\你的用户名\.claude\settings.json
```
	{
  "env": {
    "ANTHROPIC_API_KEY": "ollama",
    "ANTHROPIC_BASE_URL": "http://localhost:11434"
  }
}
```


##### 通过启动 ollama，启动 claude code
###### 启动并选择模型（交互式菜单）
	`ollama launch claude`
###### 或直接指定本地模型
	`ollama launch claude --model qwen3.5`
###### 或指定云端模型（Ollama 云，有免费额度）
	`ollama launch claude --model kimi-k2.5:cloud`


##### 在项目路径下启动 Claude code
Claude Code CLI 的工作目录（working directory / project root）
1. CMD 里切换路径
	1. `cd "C:\...."`
2. 运行 claude code
	1. `claude "analyze this project"` 
		1. 使用默认 claude 模型，默认 provider（Anthropic API），如果没有，就会报错
	2. `claude --model qwen3-coder:480b-cloud`
		1. claude code 会自动识别这个不是 Anthropic 的模型，然后查找之前配置的 provider - ollama, 然后将请求发送给本地 ollama 模型
	3. `ollama launch claude --model qwen3-coder:480b-cloud`
		1. ollama 作为入口，启动 claude 风格的代理，然后调用 ollama 自己的模型
		2. ollama 变成了主控框架，而cluade CLI 的原生能力可能受限
		3. 相当于是 ollama 系统在模拟 claude code
##### 常用指令
1. 启动：
	1. `Claude`
		1. There's an issue with the selected model (claude-sonnet-4-6). It may not exist or you may not have access to it. Run /model to pick a different model.
	2. `claude --model qwen3-coder:480b-cloud`
	3. `claude --model deepseek-v3.1:671b-cloud`
2. 创建新项目
	1. mkdir project-name
	2. cd project-name
	3. claude
3. 查看帮助：/help
4. 回退版本：/rewind
5. 清空对话：/clear
6. 退出：/exit

##### 模型调用
~/.claude/settings.json
1. Ollama
	1. 打开本地 ollama
	2. 切换 settings.json
	3. 注意每周上限
2. Zhipu glm
	1. 切换 settings.json
	2. 注意免费额度使用
3. AzureOpenAI
	1. 打开 cc Switch
	2. 打开本地代理
	3. enable AzureOpenAI
