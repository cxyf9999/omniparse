跳至主要内容
导航菜单

法典
问题
55
摄取、解析和优化从文档到多媒体➡️的任何数据格式➡️，以增强与 GenAI 框架的兼容性

omniparse.cognitivelab.in/
许可证
GPL-3.0 许可证
行为准则
行为准则
 6.2k 星
 509 个叉子
 39 正在观看
 1 个分支
 0 标签
 活动
公共存储库
Adithya-s-k/Omniparse
Name	
阿迪西娅-S-K
阿迪西娅-S-K
3 months ago
.github
5 months ago
文档
3 months ago
例子
8 months ago
Omniparse
7 months ago
python-sdk 的
7 months ago
.gitignore
8 months ago
CODE_OF_CONDUCT.md
6 months ago
Dockerfile 文件
8 months ago
许可证
7 months ago
README.md
3 months ago
存储库文件导航
自述文件
OmniParse 系列
OmniParse GitHub Stars GitHub Forks GitHub Issues GitHub Pull Requests License

重要

OmniParse 是一个平台，可将任何非结构化数据提取并解析为针对 GenAI （LLM） 应用程序优化的结构化、可作数据。无论您是在处理文档、表格、图像、视频、音频文件还是网页，OmniParse 都会让您的数据变得干净、结构化，并为 RAG 等 AI 应用程序做好准备

试用
Open In Colab

介绍
 OmniParse.1.mp4 
特征
✅ 完全本地，无需外部 API
✅ 适合 T4 GPU
✅ 支持 ~20 文件类型
✅ 将文档、多媒体和网页转换为高质量的结构化 markdown
✅ 表格提取、图像提取/字幕、音频/视频转录、网页爬取
✅ 使用 Docker 和 Skypilot
✅ Colab
✅ 友好型 由 Gradio 提供支持的交互式 UI 轻松部署

为什么选择 OmniParse ？
处理数据具有挑战性，因为它具有不同的形状和大小。OmniParse 旨在成为一个摄取/解析平台，您可以在其中摄取任何类型的数据，例如文档、图像、音频、视频和 Web 内容，并获得对 GenAI （LLM） 友好的最结构化和可作的输出。

安装
重要

该服务器仅适用于基于 Linux 的系统。这是由于某些依赖项和特定于系统的配置与 Windows 或 macOS 不兼容。

git clone https://github.com/adithya-s-k/omniparse
cd omniparse
创建虚拟环境：

conda create -n omniparse-venv python=3.10
conda activate omniparse-venv
安装依赖项：

poetry install
# or
pip install -e .
# or
pip install -r pyproject.toml
🛳️ 码头工人
要将 OmniParse 与 Docker 结合使用，请执行以下命令：

从 Docker Hub 中提取 OmniParse API Docker 镜像：
运行 Docker 容器，公开端口 8000： 👉🏼Docker 镜像
docker pull savatar101/omniparse:0.1
# if you are running on a gpu 
docker run --gpus all -p 8000:8000 savatar101/omniparse:0.1
# else
docker run -p 8000:8000 savatar101/omniparse:0.1
或者，如果您希望在本地构建 Docker 镜像： 然后，运行 Docker 容器，如下所示：

docker build -t omniparse .
# if you are running on a gpu
docker run --gpus all -p 8000:8000 omniparse
# else
docker run -p 8000:8000 omniparse
用法
运行服务器：

python server.py --host 0.0.0.0 --port 8000 --documents --media --web
--documents：加载所有可帮助您解析和摄取文档的模型（Surya OCR 系列模型和 Florence-2）。
--media：加载 Whisper 模型以转录音频和视频文件。
--web：设置 selenium crawler。
下载模型： 如果要在启动服务器之前下载模型

python download.py --documents --media --web
--documents：加载所有可帮助您解析和摄取文档的模型（Surya OCR 系列模型和 Florence-2）。
--media：加载 Whisper 模型以转录音频和视频文件。
--web：设置 selenium crawler。
支持的数据类型
类型	支持的扩展
文件	.doc、.docx、.pdf、.ppt .pptx
图像	.png、.jpg、.jpeg、.tiff、.bmp .heic
视频	.mp4、.mkv、.avi .mov
音频	.mp3、.wav、.aac
蹼	动态网页，http：//.com
API 端点
即将推出/ 路线图
🦙 美洲驼索引 |Langchain |Haystack 集成即将推出 📚 批处理数据 ⭐ 基于指定 Schema
🛠️ One magic API 的动态分块和结构化数据提取：只需在文件中输入提示您想要的内容，剩下的
🔧交给我们 动态模型选择和对外部 API
📄 的支持 一次处理多个文件的
📦批处理 新的开源模型取代 Surya OCR 和 Marker

最终目标：用单个 MultiModel Model 替换当前使用的所有不同模型，以解析任何类型的数据并获取所需的数据。

局限性
由于我们正在使用深度学习模型，因此需要最低 8~10 GB VRAM 的 GPU。 \

文档解析限制 \

Marker 是底层的 PDF 解析器，它不会将 100% 的方程式转换为 LaTeX，因为它必须检测然后转换它们。
它擅长解析英语，但可能难以解析中文等语言
表格的格式并不总是 100% 正确;text 可以位于错误的列中。
空格和缩进并不总是得到尊重。
并非所有的线/跨度都会正确连接。
这在不需要大量 OCR 的数字 PDF 上效果最佳。它针对速度进行了优化，并使用有限的 OCR 来修复错误。
为了适应 GPU 中的所有模型，我们使用了最小的变体，这些变体可能无法提供一流的性能。
许可证
OmniParse 根据 GPL-3.0 许可证获得许可。有关更多信息，请参阅。 该项目在后台使用了 Marker，它有一个需要遵循的商业许可证。以下是详细信息：LICENSE

商业用途
Marker 和 Surya OCR 模型旨在尽可能广泛地访问，同时仍为开发和培训成本提供资金。研究和个人使用始终是允许的，但对商业使用有一些限制。 模型的权重根据 cc-by-nc-sa-4.0 获得许可。但是，对于最近 12 个月总收入低于 $5M USD 且终身筹集的 VC/天使资金少于 $5M 的任何组织，都可以免除此限制。要删除 GPL 许可证要求（双重许可证）和/或商业上使用超过收入限制的权重，请查看提供的选项。 请参阅 Marker 以获取有关模型权重许可证的更多信息

确认
该项目建立在 Vik Paruchuri 创建的非凡的 Marker 项目之上。我们对该项目提供的灵感和基础表示感谢。特别感谢 Surya-OCR 和 Texify 在本项目中广泛使用的 OCR 模型，以及 Crawl4AI 的贡献。

使用的型号：

Surya OCR、检测、布局、排序和纹理化
佛罗伦萨-2 基地
Whisper 小号
感谢作者对这些模型的贡献。

联系
Star History Chart

如有任何疑问，请通过 adithyaskolavi@gmail.com 与我们联系
释放
未发布版本
包
未发布包
贡献
5
@adithya-s-k
@yangfuhai
@hillkim
@AswanthManoj
@moria97
语言
蟒
98.4%
 
Dockerfile 文件
1.6%
页脚
© 2025 年 GitHub， Inc.
页脚导航
条款
隐私
安全
地位
文档
联系
管理 Cookie
不要分享我的个人信息
