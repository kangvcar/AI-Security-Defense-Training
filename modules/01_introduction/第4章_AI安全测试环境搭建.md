# 第 4 章：AI 安全测试环境搭建

**章节目标**
- 掌握阿里云天池 Notebook 的基本操作
- 完成 Python 环境配置与依赖安装
- 验证核心库（transformers、torch、numpy、matplotlib）的正确安装
- 学会排查常见环境问题
- 为后续实验做好准备

---

## 1. 为什么选择天池 Notebook？（占比 15%）

### 1.1 在线实验环境的优势

**传统本地环境的痛点**：
- 显卡配置不足：AI 模型需要 GPU 加速，普通电脑难以满足
- 环境配置复杂：CUDA、cuDNN、PyTorch 版本兼容问题让人头疼
- 资源消耗大：大语言模型动辄需要 8GB 以上显存

**天池 Notebook 的解决方案**：

| 特性 | 说明 | 对学习的帮助 |
|------|------|-------------|
| **免费 GPU** | 提供 Tesla T4 等 GPU 资源 | 可以运行中等规模的 AI 模型 |
| **预装环境** | Python、PyTorch 等已配置好 | 省去繁琐的安装步骤 |
| **云端存储** | 代码和数据保存在云端 | 随时随地继续学习 |
| **即开即用** | 浏览器打开就能编程 | 无需本地安装任何软件 |

**类比**：天池 Notebook 就像一个**云端实验室**——你不需要自己买设备、搭环境，直接走进实验室就能开始做实验。

### 1.2 其他可选平台

如果天池不可用，以下平台也可以使用：

| 平台 | 免费额度 | GPU 支持 | 适合场景 |
|------|---------|----------|---------|
| 阿里云天池 | 每周约 30 小时 | Tesla T4 | 本课程首选 |
| Google Colab | 每日有限额度 | Tesla T4/K80 | 需科学上网 |
| Kaggle Notebooks | 每周 30 小时 | Tesla P100 | 国际比赛平台 |
| 百度飞桨 AI Studio | 每日 8 小时 | Tesla V100 | 国产替代方案 |

---

## 2. 天池 Notebook 操作指南（占比 35%）

### 2.1 注册与登录

**步骤 1：访问天池平台**
- 打开浏览器，访问 https://tianchi.aliyun.com/
- 点击右上角「登录/注册」

**步骤 2：创建账号**
- 推荐使用支付宝扫码登录（最快捷）
- 也可以使用阿里云账号或手机号注册

**步骤 3：进入 Notebook 环境**
- 登录后，点击顶部菜单「天池实验室」
- 选择「Notebook」
- 点击「创建 Notebook」

### 2.2 创建第一个 Notebook

**配置选项说明**：

```
Notebook 名称：AI_Security_Lab（建议使用英文，避免中文路径问题）
镜像选择：推荐选择 PyTorch 2.0 + Python 3.10
资源配置：
  - CPU 版本：适合简单实验，启动快
  - GPU 版本：运行 AI 模型必选（本课程需要）
```

**重要提示**：
- GPU 资源有限，请在需要时再开启
- 长时间不操作会自动关闭，记得保存代码
- 每周 GPU 时长有限额，合理规划使用

### 2.3 Notebook 界面介绍

**Jupyter Notebook 基本概念**：

Jupyter Notebook 是一种**交互式编程环境**，特点是：
- 代码分成一个个「单元格（Cell）」
- 每个单元格可以单独运行
- 运行结果直接显示在单元格下方
- 支持 Markdown 格式的文字说明

**常用快捷键**：

| 快捷键 | 功能 | 使用场景 |
|--------|------|---------|
| `Shift + Enter` | 运行当前单元格并跳到下一个 | 最常用的运行方式 |
| `Ctrl + Enter` | 运行当前单元格（不跳转） | 反复调试同一段代码 |
| `Esc + A` | 在上方插入新单元格 | 添加代码或说明 |
| `Esc + B` | 在下方插入新单元格 | 添加代码或说明 |
| `Esc + M` | 将单元格转为 Markdown | 写文字说明 |
| `Esc + Y` | 将单元格转为代码 | 写 Python 代码 |
| `Esc + DD` | 删除当前单元格 | 清理不需要的内容 |

**类比**：Jupyter Notebook 就像一本**可执行的笔记本**——你可以在里面写笔记，也可以写代码并立即看到结果。

### 2.4 文件管理

**上传文件**：
- 点击左侧文件浏览器的「上传」按钮
- 或直接拖拽文件到文件列表区域

**下载文件**：
- 右键点击文件，选择「下载」

**注意事项**：
- 天池 Notebook 每次启动会分配临时空间
- 重要文件请保存到 `/home/admin/` 目录
- 也可以挂载 OSS 存储（高级用法）

---

## 3. Python 环境与依赖安装（占比 30%）

### 3.1 本课程核心依赖

本课程所有实验只使用以下 4 个核心库：

```python
# 核心依赖（天池已预装，通常无需手动安装）
transformers  # Hugging Face 的 Transformer 模型库
torch         # PyTorch 深度学习框架
numpy         # 数值计算库
matplotlib    # 数据可视化库
```

**为什么只用这 4 个库？**
- **降低门槛**：减少环境配置问题
- **稳定可靠**：都是成熟的主流库
- **覆盖需求**：足以完成所有实验

### 3.2 环境验证脚本

**在 Notebook 中运行以下代码，验证环境是否正常**：

```python
# ====== 环境验证脚本 ======
# 运行这段代码检查所有依赖是否正确安装

print("=" * 50)
print("AI 安全实验环境检查")
print("=" * 50)

# 检查 1：Python 版本
import sys
print(f"\n[1] Python 版本: {sys.version}")
assert sys.version_info >= (3, 8), "需要 Python 3.8 或更高版本"
print("    ✓ Python 版本符合要求")

# 检查 2：PyTorch
import torch
print(f"\n[2] PyTorch 版本: {torch.__version__}")
print(f"    CUDA 可用: {torch.cuda.is_available()}")
if torch.cuda.is_available():
    print(f"    GPU 型号: {torch.cuda.get_device_name(0)}")
print("    ✓ PyTorch 安装正常")

# 检查 3：Transformers
import transformers
print(f"\n[3] Transformers 版本: {transformers.__version__}")
print("    ✓ Transformers 安装正常")

# 检查 4：NumPy
import numpy as np
print(f"\n[4] NumPy 版本: {np.__version__}")
print("    ✓ NumPy 安装正常")

# 检查 5：Matplotlib
import matplotlib
print(f"\n[5] Matplotlib 版本: {matplotlib.__version__}")
print("    ✓ Matplotlib 安装正常")

print("\n" + "=" * 50)
print("🎉 恭喜！所有依赖检查通过，环境配置正确！")
print("=" * 50)
```

**预期输出示例**：

```
==================================================
AI 安全实验环境检查
==================================================

[1] Python 版本: 3.10.12 (main, Jun 11 2023, 05:26:28)
    ✓ Python 版本符合要求

[2] PyTorch 版本: 2.0.1
    CUDA 可用: True
    GPU 型号: Tesla T4
    ✓ PyTorch 安装正常

[3] Transformers 版本: 4.35.0
    ✓ Transformers 安装正常

[4] NumPy 版本: 1.24.3
    ✓ NumPy 安装正常

[5] Matplotlib 版本: 3.7.1
    ✓ Matplotlib 安装正常

==================================================
🎉 恭喜！所有依赖检查通过，环境配置正确！
==================================================
```

### 3.3 手动安装依赖（如果缺失）

如果某个库未安装或版本过旧，使用以下命令安装：

```python
# 在 Notebook 单元格中运行（注意前面的感叹号）
!pip install transformers==4.35.0 -i https://mirrors.aliyun.com/pypi/simple/
!pip install torch==2.0.1 -i https://mirrors.aliyun.com/pypi/simple/
!pip install numpy==1.24.3 -i https://mirrors.aliyun.com/pypi/simple/
!pip install matplotlib==3.7.1 -i https://mirrors.aliyun.com/pypi/simple/
```

**说明**：
- `!` 前缀表示在 Notebook 中执行 Shell 命令
- `-i https://mirrors.aliyun.com/pypi/simple/` 使用阿里云镜像，下载更快

### 3.4 第一个 AI 模型调用

**验证模型加载能力**：

```python
# ====== 测试模型加载 ======
# 这段代码测试能否正常加载和使用 AI 模型

from transformers import pipeline

# 加载一个轻量级的情感分析模型（约 500MB）
# 首次运行会下载模型，请耐心等待
print("正在加载模型...")
classifier = pipeline("sentiment-analysis", model="distilbert-base-uncased-finetuned-sst-2-english")

# 测试模型
test_text = "I love learning AI security!"
result = classifier(test_text)

print(f"\n测试文本: {test_text}")
print(f"分析结果: {result}")
print("\n✓ 模型加载和推理正常！")
```

**预期输出**：

```
正在加载模型...

测试文本: I love learning AI security!
分析结果: [{'label': 'POSITIVE', 'score': 0.9998}]

✓ 模型加载和推理正常！
```

---

## 4. 常见问题排查（占比 20%）

### 4.1 GPU 相关问题

**问题 1：CUDA 不可用**

```python
# 症状
torch.cuda.is_available()  # 返回 False
```

**解决方案**：
- 确认创建 Notebook 时选择了 GPU 资源
- 如果选择了 CPU 版本，需要重新创建 Notebook
- 检查 GPU 资源是否已用完（每周有限额）

**问题 2：GPU 内存不足**

```
CUDA out of memory. Tried to allocate X MiB
```

**解决方案**：
```python
# 方法 1：清理 GPU 缓存
import torch
torch.cuda.empty_cache()

# 方法 2：重启 Notebook 内核
# 点击菜单 Kernel → Restart Kernel

# 方法 3：使用更小的模型
# 在本课程中，我们选择的模型都已经过优化
```

### 4.2 模型下载问题

**问题 3：模型下载超时**

```
ConnectionError: HTTPSConnectionPool timeout
```

**解决方案**：
```python
# 方法 1：设置国内镜像
import os
os.environ['HF_ENDPOINT'] = 'https://hf-mirror.com'

# 方法 2：重试几次（网络波动导致）

# 方法 3：使用离线模型（课程会提供）
```

**问题 4：模型不存在**

```
OSError: Can't load model 'xxx'. Model doesn't exist
```

**解决方案**：
- 检查模型名称拼写是否正确
- 确认网络连接正常
- 尝试使用完整的模型路径

### 4.3 依赖冲突问题

**问题 5：版本不兼容**

```
ImportError: cannot import name 'xxx' from 'transformers'
```

**解决方案**：
```python
# 查看当前版本
!pip show transformers

# 安装指定版本
!pip install transformers==4.35.0 --force-reinstall

# 重启内核使更改生效
# 点击菜单 Kernel → Restart Kernel
```

### 4.4 快速诊断清单

遇到问题时，按以下顺序排查：

| 步骤 | 检查项 | 命令/操作 |
|------|--------|----------|
| 1 | Python 版本 | `import sys; print(sys.version)` |
| 2 | GPU 可用性 | `import torch; print(torch.cuda.is_available())` |
| 3 | 依赖版本 | `!pip list \| grep -E "torch\|transformers"` |
| 4 | 网络连接 | `!ping hf-mirror.com` |
| 5 | 重启内核 | Kernel → Restart Kernel |
| 6 | 重建 Notebook | 创建新的 Notebook 实例 |

---

## 教学资源

**官方文档**：
- 天池 Notebook 帮助文档：https://tianchi.aliyun.com/notebook-ai/
- Hugging Face 中文文档：https://huggingface.co/docs
- PyTorch 官方教程：https://pytorch.org/tutorials/

**视频教程**：
- B 站搜索「Jupyter Notebook 入门」
- B 站搜索「天池 Notebook 使用教程」

**常用资源**：
- Hugging Face 模型库：https://huggingface.co/models
- 国内镜像：https://hf-mirror.com

---

## 课后思考题

**思考题 1（理解性问题）**：
为什么本课程选择在线 Notebook 环境而不是本地安装？请从硬件资源、环境配置、学习效率三个角度分析。

**思考题 2（实践性问题）**：
运行环境验证脚本后，如果发现 CUDA 不可用（torch.cuda.is_available() 返回 False），请列出至少 3 种可能的原因和对应的解决方案。

**思考题 3（扩展性问题）**：
除了天池 Notebook，还有哪些平台可以用于 AI 实验？请对比它们的优缺点，并说明在什么情况下你会选择其他平台。

---

## 本章小结

通过本章学习，你应该已经完成了实验环境的搭建：

✅ **平台选择**：了解天池 Notebook 的优势，学会创建和使用 Notebook
✅ **基本操作**：掌握 Jupyter Notebook 的界面和常用快捷键
✅ **环境配置**：安装并验证了 4 个核心依赖库
✅ **问题排查**：学会了常见问题的诊断和解决方法

**关键认知**：
> 环境搭建是实验的基础。一个稳定、正确配置的环境能让你专注于学习 AI 安全知识，而不是被技术问题困扰。

**下一步**：
在 [第 5 章：AI 漏洞探测初体验](第5章_AI漏洞探测初体验.md) 中，我们将开始动手探测 AI 模型的潜在漏洞。

**实验衔接**：
本章内容与 [实验 1.1：环境搭建与模型调用](../labs/lab1_1_environment_setup.ipynb) 紧密配合。请在完成本章阅读后，立即进行实验 1.1，巩固所学内容。

---

## 环境检查清单

在进入下一章之前，请确认以下事项：

- [ ] 成功创建天池 Notebook（GPU 版本）
- [ ] 运行环境验证脚本，所有检查通过
- [ ] 成功加载并运行测试模型
- [ ] 熟悉 Jupyter Notebook 基本操作
- [ ] 收藏常见问题解决方案

**如果所有项目都已完成，恭喜你！你已经准备好开始 AI 安全实验了！**
