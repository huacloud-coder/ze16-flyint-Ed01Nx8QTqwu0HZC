
![](https://img2024.cnblogs.com/blog/1769816/202411/1769816-20241126100521163-451898759.png)


## 一、SpringAI 简介


随着人工智能技术的飞速发展，越来越多的开发者开始探索如何将 `AI` 能力集成到现有的应用中来提升产品的智能化水平。`Spring AI` 正是为 `Java` 开发者提供的一款强大的 `AI` 框架，使得这一集成过程变得前所未有的简单和高效。


本文将深入探讨 `Spring AI` 的核心概念以及如何快速上手使用这款智能新利器。


## 二、什么是Spring AI？


目前 `AI` 应用程序开发框架主要是 `Python` 生态；而 `Spring AI` 是由 `Spring` 团队推出的一个扩展框架，专为将 `AI` 能力集成到 `Java` 应用中而设计。它利用 `Spring` 的生态系统优势，提供了一系列简单易用的 `API` 和工具，使开发者可以轻松地加载、训练和推理 `AI模型`。这不仅降低了开发门槛，还极大地提高了开发效率。


![](https://img2024.cnblogs.com/blog/1769816/202411/1769816-20241126100521758-1347544623.png)


`Spring AI` 的核心是解决 `AI` 集成的根本挑战：**将您的企业数据和 API 与 AI 模型连接起来。**


## 三、Spring AI的核心概念


### 3\.1\. Models


**模型**（Models）是指在处理和生成信息的算法，通常模仿人类认知功能。通过从大型数据集中学习模式和见解，这些模型可以做出预测、文本、图像或其他输出，增强跨行业的各种应用。


`Spring AI` 支持多种 `AI模型` 包括神经网络、决策树等。模型可以通过训练数据进行训练，之后用于推理。


![](https://img2024.cnblogs.com/blog/1769816/202411/1769816-20241126100522176-1520856911.png)


### 3\.2\. Prompts


**提示**（Prompts）是基于语言输入的基础，指导 `AI` 模型生成特定输出。对于熟悉 `ChatGPT` 的人来说，提示可能看起来只是输入对话框中的文本，传送到 `API` 然而，它的内涵远不止于此，在许多 `AI` 模型中，提示文本并不只是一个简单的字符串。


在 `ChatGPT` 的 `API` 中，一个提示包含多个文本输入，每个输入都会被赋予不同的角色。例如，有一个 **系统角色** 它告诉模型如何行为并设定互动的上下文。此外，还有一个 **用户角色** 通常就是用户的输入。


设计有效的提示既是一门艺术，也是一门科学。`ChatGPT` 被设计用于人类对话，这与使用 `SQL` 等语言 **提问** 的方式有很大不同。与 `AI` 模型交流更像是与另一个人对话。


### 3\.3\. Embeddings


**嵌入**（Embeddings）是文本、图像或视频的数值表示，用于捕捉输入之间的关系。


嵌入通过将文本、图像和视频转换为浮点数数组（称为向量）来工作。这些向量旨在捕捉文本、图像和视频的含义。嵌入数组的长度被称为向量的维度。


通过计算两个文本的向量表示之间的数值距离，应用程序可以判断生成这些嵌入向量的对象之间的相似性。


![](https://img2024.cnblogs.com/blog/1769816/202411/1769816-20241126100522662-2049471665.png)


### 3\.4\. Tokens


**令牌**（Tokens）是 `AI` 模型工作的基础构件。输入时，模型会将单词转换为令牌；输出时，模型会将令牌重新转换为单词。


![](https://img2024.cnblogs.com/blog/1769816/202411/1769816-20241126100523103-1717446567.png)


### 3\.5\. Structured Output


`AI` 模型的输出通常以 `java.lang.String` 的形式返回，即使你要求回复为 `JSON` 格式，但它并不是一个 `JSON` 数据结构，而只是一个字符串。


这一复杂性催生了一个专门的领域，涉及创建提示以获得预期输出，然后将生成的简单字符串转换为可用于应用集成的数据结构。


![](https://img2024.cnblogs.com/blog/1769816/202411/1769816-20241126100523488-576968856.png)


### 3\.6\. Bringing Your Data \& APIs to the AI Model


如何让 `AI` 模型掌握它未被训练过的信息？


目前有三种方法可以定制 `AI` 模型以整合您的数据：


* **微调**（Fine Tuning）：这种传统的机器学习技术涉及调整模型，并改变其内部权重。然而非常耗费资源。此外，有些模型可能不支持这一选项。
* **提示嵌入**（Prompt Stuffing）：一种更实际的替代方案是将您的数据嵌入提供给模型的提示中。
* **函数调用**（Function Calling）：这种技术允许注册自定义的用户函数，将大型语言模型与外部系统的 API 连接起来。


![](https://img2024.cnblogs.com/blog/1769816/202411/1769816-20241126100523949-1120856682.png)


### 3\.7\. Retrieval Augmented Generation


`RAG` 是一种称为 **检索增强生成** 的技术，用以解决如何将相关数据整合到提示中以确保 `AI` 模型能够给出准确的回答。


这种方法涉及一种批处理风格的编程模型，其中任务从文档中读取非结构化数据，进行转换，然后将其写入向量数据库。从宏观角度看，这类似于一个 `ETL`（提取、转换和加载）管道。向量数据库用于 `RAG` 技术中的检索部分。


![](https://img2024.cnblogs.com/blog/1769816/202411/1769816-20241126100524544-549255626.png)


## 四、快速上手指南



> 注意 Spring AI 支持 Spring Boot 3\.2\. x 和 3\.3\.x


**Maven 仓库配置**
在 `pom.xml` 中添加以下内容：



```
<repositories>
  <repository>
    <id>spring-milestonesid>
    <name>Spring Milestonesname>
    <url>https://repo.spring.io/milestoneurl>
    <snapshots>
      <enabled>falseenabled>
    snapshots>
  repository>
  <repository>
    <id>spring-snapshotsid>
    <name>Spring Snapshotsname>
    <url>https://repo.spring.io/snapshoturl>
    <releases>
      <enabled>falseenabled>
    releases>
  repository>
repositories>

```

**导入 Spring AI BOM**



```
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>org.springframework.aigroupId>
            <artifactId>spring-ai-bomartifactId>
            <version>1.0.0-SNAPSHOTversion>
            <type>pomtype>
            <scope>importscope>
        dependency>
    dependencies>
dependencyManagement>

```

**添加 OpenAI 聊天**



```
<dependency>
    <groupId>org.springframework.aigroupId>
    <artifactId>spring-ai-openai-spring-boot-starterartifactId>
dependency>

```


> 使用 OpenAI 创建 API 来访问 ChatGPT 模型。在OpenAI 注册页面创建账户并在API 密钥页面生成令牌。


**代码样例**



```
@RestController
public class EmbeddingApiController {
    @Resource
    private EmbeddingClient client;

    @GetMapping("/api/v1/embedding")
    public Map getEmbedding(@RequestParam(name = "message", defaultValue = "Share a funny story") String input) {
        EmbeddingResponse response = client.embedForResponse(Collections.singletonList(input));
        return Collections.singletonMap("embedding", response);
    }
}

```

## 总结


`SpringAI` 无疑是 `Java` 开发领域在人工智能方向上的重要创新。它将 `Spring Framework` 的优势与先进的 `AI` 技术完美融合，通过其关键特性在多个方面为开发者提供了强大的助力。


 本博客参考[milou加速器](https://xinminxuehui.org)。转载请注明出处！
