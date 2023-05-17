# privateGPT
在没有互联网连接的情况下，使用LLMs的能力向你的文档提问。100％私密，没有任何数据在任何时候离开你的执行环境。你可以导入文档并在没有互联网连接的情况下提问！


下载下面这两个东西，并放进models文件夹中
Built with [LangChain](https://github.com/hwchase17/langchain) and [GPT4All](https://github.com/nomic-ai/gpt4all) and [LlamaCpp](https://github.com/ggerganov/llama.cpp)

<img width="902" alt="demo" src="https://user-images.githubusercontent.com/721666/236942256-985801c9-25b9-48ef-80be-3acbb4575164.png">

# Environment Setup
为了设置你的环境以运行此处的代码，请先安装所有的依赖项：

```shell
pip install -r requirements.txt
```

将 `example.env` 重命名为 `.env`。

注意：不要放在有中文的目录下


## Instructions for ingesting your own dataset

把你的文件放入 `source_documents` 目录中。

The supported extensions are:

   - `.csv`: CSV,
   - `.docx`: Word Document,
   - `.enex`: EverNote,
   - `.eml`: Email,
   - `.epub`: EPub,
   - `.html`: HTML File,
   - `.md`: Markdown,
   - `.msg`: Outlook Message,
   - `.odt`: Open Document Text,
   - `.pdf`: Portable Document Format (PDF),
   - `.pptx` : PowerPoint Document,
   - `.txt`: Text file (UTF-8),

运行ingest.py是在处理你输入的文件
```shell
python ingest.py
```

它将创建一个包含本地向量存储的 `db` 文件夹。这需要时间，具体取决于你的文档大小。
你可以导入任意数量的文档，并且所有文档都将累积在本地嵌入数据库中。
如果你想从空数据库开始，请删除 `db` 文件夹。



## Ask questions to your documents, locally!
问问题可以运行privateGPT.py

```shell
python privateGPT.py
```

And wait for the script to require your input. 

```plaintext
> Enter a query:
```

按回车键。你需要等待20-30秒钟（取决于你的计算机性能），等待LLM模型消耗提示并准备好答案。完成后，它将打印答案以及它从你的文档中使用的4个上下文源；然后你可以继续提问而无需重新运行脚本，只需等待提示即可。

注意：即使断开互联网连接，脚本的推理仍然可以工作。没有任何数据会离开你的本地环境。

输入 `exit` 来结束脚本运行。


# System Requirements

## Python Version
要使用此软件，必须安装 Python 3.10 或更高版本。早期版本的 Python 将无法编译。

这里我使用的是anaconda创建python3.10环境

## C++ Compiler
如果在 `pip install` 过程中构建 wheel 时遇到错误，你可能需要在你的计算机上安装 C++ 编译器。



# Disclaimer
这是一个测试项目，旨在验证使用LLMs和向量嵌入的完全私密的问答解决方案的可行性。它不准备用于生产环境，也不具备生产环境的可用性。模型的选择并非针对性能进行优化，而是为了保护隐私。但是，可以使用不同的模型和向量存储库来提高性能。
