[TOC]
# 部署
## 准备工作
安装lfs以便下载git文件指针指向的文件
```
sudo apt install git-lfs
```
## 下载模型
### llama3.2-3B模型
```
git clone https://www.modelscope.cn/LLM-Research/Llama-3.2-3B-Instruct.git
```
### Qwen2.5-3B模型
```
git clone https://www.modelscope.cn/Qwen/Qwen2.5-3B-Instruct.git
```

## 编译安装 llama.cpp

### 下载代码
```
git clone https://github.com/ggerganov/llama.cpp
```

### 编译(cuda方式)
#### 安装软件包

```
sudo apt install nvidia-cuda-toolkit

```

#### 带cuda编译llama.cpp
```
cmake -B build_llama_cpp  -DGGML_CUDA=ON llama.cpp
cmake --build build_llama_cpp --config Release -j
```

### 编译(cpu方式)
```
cmake -B build_llama_cpp llama.cpp
cmake --build build_llama_cpp --config Release -j
```

## 运行
### 转换模型格式
```
python3 llama.cpp/convert_hf_to_gguf.py Llama-3.2-3B-Instruct
```

### 启动llama
```
build_llama_cpp/bin/llama-server -ngl 30 -m Llama-3.2-3B-Instruct/Llama-3.2-3B-Instruct-F16.gguf
```
