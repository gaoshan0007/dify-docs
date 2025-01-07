# 创建知识库

创建知识库并上传文档大致分为以下步骤：

1. 创建知识库。通过上传本地文件、导入在线数据或创建一个空的知识库。

{% content-ref url="import-content-data/" %}
[import-content-data](import-content-data/)
{% endcontent-ref %}

2. 指定分段模式。该阶段是内容的预处理与数据结构化过程，长文本将会被划分为多个内容分段。你可以在此环节预览文本的分段效果。

{% content-ref url="chunking-and-cleaning-text.md" %}
[chunking-and-cleaning-text.md](chunking-and-cleaning-text.md)
{% endcontent-ref %}

3. 设定索引方法和检索设置。知识库在接收到用户查询问题后，按照预设的检索方式在已有的文档内查找相关内容，提取出高度相关的信息片段供语言模型生成高质量答案。

{% content-ref url="setting-indexing-methods.md" %}
[setting-indexing-methods.md](setting-indexing-methods.md)
{% endcontent-ref %}

5. 等待分段嵌入
6. 完成上传，在应用内关联知识库并使用。你可以参考[在应用内集成知识库](../integrate-knowledge-within-application.md)，搭建出能够基于知识库进行问答的 LLM 应用。如需修改或管理知识库，请参考[知识库管理与文档维护](../knowledge-and-documents-maintenance/)。

![完成知识库的创建](https://assets-docs.dify.ai/2024/12/a3362a1cd384cb2b539c9858de555518.png)

***

### 参考阅读

#### ETL

在 RAG 的生产级应用中，为了获得更好的数据召回效果，需要对多源数据进行预处理和清洗，即 ETL （_extract, transform, load_）。为了增强非结构化/半结构化数据的预处理能力，Dify 支持了可选的 ETL 方案：**Dify ETL** 和[ ](https://docs.unstructured.io/welcome)[**Unstructured ETL** ](https://unstructured.io/)。Unstructured 能够高效地提取并转换你的数据为干净的数据用于后续的步骤。Dify 各版本的 ETL 方案选择：

* SaaS 版不可选，默认使用 Unstructured ETL；
* 社区版可选，默认使用 Dify ETL ，可通过[环境变量](https://docs.dify.ai/v/zh-hans/getting-started/install-self-hosted/environments#zhi-shi-ku-pei-zhi)开启 Unstructured ETL；

文件解析支持格式的差异：

| DIFY ETL                                       | Unstructured ETL                                                         |
| ---------------------------------------------- | ------------------------------------------------------------------------ |
| txt、markdown、md、pdf、html、htm、xlsx、xls、docx、csv | txt、markdown、md、pdf、html、htm、xlsx、xls、docx、csv、eml、msg、pptx、ppt、xml、epub |

不同的 ETL 方案在文件提取效果的方面也会存在差异，想了解更多关于 Unstructured ETL 的数据处理方式，请参考[官方文档](https://docs.unstructured.io/open-source/core-functionality/partitioning)。

***

#### **Embedding**

**Embedding 嵌入**是一种将离散型变量（如单词、句子或者整个文档）转化为连续的向量表示的技术。它可以将高维数据（如单词、短语或图像）映射到低维空间，提供一种紧凑且有效的表示方式。这种表示不仅减少了数据的维度，还保留了重要的语义信息，使得后续的内容检索更加高效。

**Embedding 模型**是一种专门用于将文本向量化的大语言模型，它擅长将文本转换为密集的数值向量，有效捕捉语义信息。

> 如需了解更多，请参考：[《Dify：Embedding 技术与 Dify 知识库设计/规划》](https://mp.weixin.qq.com/s/vmY_CUmETo2IpEBf1nEGLQ)。