# 前端
这里使用了llama.cpp项目的examples/server/public/index.html文件作为前端。在aiohttp中把它映射到了web服务的根目录``http://127.0.0.1:8888/``

# 后端及大模型
用aiohttp代理了llama.cpp的问答请求，在llama.cpp中运行的是Qwen2.5-3B-Instruct模型。
通过aiohttp把部署在``http://127.0.0.1:8080/v1/chat/completions``的llama.cpp映射到aiohttp服务的``http://127.0.0.1:8888/v1/chat/completions``为实现打字效果，使用了aiohttp的``aiohttp.web.StreamResponse``响应类

# 引用了jieba分词
```
pip3 install jieba
```