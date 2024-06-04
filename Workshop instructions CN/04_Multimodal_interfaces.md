# 第三部分 - 多模态界面

到目前为止，我们已经使用单一模态与 LLM 进行了交互：输入文本并接收文本或图像。然而，多模态界面正变得越来越流行，因为它们允许用户使用多种模态（例如文本、图像和语音）与模型进行交互，从而促进人机交互。在本节中，我们将探讨如何使用多模态界面与 GPT-4 Turbo with Vision 进行交互。

> [!TIP]
> **GPT-4 Turbo with Vision** 是一个结合了自然语言处理和视觉理解的多模态模型。它能够将文本和图像的组合作为输入进行处理，并生成与两种模态相关的输出。

## 最佳实践

- **上下文特异性**：为手头的场景添加上下文可让模型更好地理解适当的输出。这种程度的特异性有助于关注相关方面并避免无关细节。​

- **面向任务的提示**：专注于特定任务有助于模型在考虑该视角的同时开发输出。​

- **定义输出格式**：明确提及输出的所需格式，例如 markdown、JSON、HTML 等。您还可以建议有关响应的特定结构、长度或特定属性。​

- **处理拒绝**：当模型表示无法执行任务时，细化提示可能是一种有效的解决方案。更具体的提示可以引导模型更清楚地理解和更好地执行任务。需要记住的一些提示：​
  - 请求对生成的响应进行解释，以增强模型输出的透明度​
  - 如果使用单图像提示，请将图像放在文本之前​
  - 要求模型首先详细描述图像，然后根据描述完成您的特定任务​

- **提示调整**：尝试我们为文本生成场景探索的提示调整技术，例如：​
  - 分解请求（例如思路链）​
  - 添加示例（例如小样本学习）​

## 使用图像与模型交互

在聊天界面中，单击附件图标上传本地图像，然后从本地桌面文件夹中选择 *contoso_outdoor_ecommerce_sketch_notes.jpg* 图像。
文件夹路径：
Documents\Workshop-Interact-with-LLMs\Workshop instructions\Images\contoso_outdoor_ecommerce_sketch_notes.jpg

![Uploading image as input](./Images/upload_image_icon.png)

如果您在 VM 的本地桌面上找不到该图像，您可以从[此处](./Images/contoso_outdoor_ecommerce_sketch_notes.jpg)下载它。

![Contoso Ecommerce Website UI](./Images/contoso_outdoor_ecommerce_sketch_notes.jpg).

此图像代表我们想要构建的 Contoso Outdoor 电子商务网站的草图。我们将使用此图像作为 GPT-4 Turbo with Vision 的输入，以从图像中收集信息，然后使用草图作为参考为网站生成代码片段。

上传文件后，请尝试以下提示开始与图像交互：

```How many products are shown in the homepage below?```


```What is the name of the company?```


```What is the most expensive product?```

## 从图像生成网站 UI 的代码片段

接下来，我们将提示模型使用草图作为参考为网站生成代码片段。
1. 转到 **参数** 选项卡并将 *最大响应* 设置为 4000。
   
2. 添加以下文本以指导模型如何使用图像输入：

```
Generate the html and bootstrap code to implement the UI of the Contoso Outdoor Company e-commerce landing page, based on the hand-drawn sketches in the image.
```

结果应提供 Contoso Outdoor Company 着陆页的基本布局。它包括产品描述的占位符，您可以使用第 1 部分和第 2 部分中创建的文本和图像工件填充这些占位符。

如果您想查看代码语法是否正确以及模板是什么样子：
1. 打开 VS Code。

2. 文件 - 新建文件 - 输入 website.html 并将其保存到桌面。

3. 将生成的 HTML 代码粘贴到空的 html 文件中。

4. 选择 V​​S Code 右上角的 **打开预览到侧面** 按钮以查看输出。

![Preview website code in VS Code](./Images/vs-code-view-html.png)


## 应用提示调整

如果您对上一步得到的结果不满意，可以应用一些提示调整技术来提高生成代码的质量。事实上，您在上一步中用来指导模型的提示已经包含了一些提示工程最佳实践，例如 *将图像放在文本之前* 并指定 *输出格式* 。但是，您可以尝试进一步优化提示以获得更好的结果。

> [!NOTE]
> 如果模型表示无法执行任务，您可以通过请求对生成的响应进行解释以及它缺少哪些信息来完成任务来**处理拒绝**。

>[!alert] 在系统消息字段中插入以下文本，然后单击“应用更改”。

```
## Task
You are a web designer for the Contoso Outdoor Company e-commerce website. Your goal is to generate the website code snippets for the homepage GUI.
```

此外，我们修改一下之前的查询，将指令分解成更小的步骤。这将有助于模型更好地理解任务并生成更准确的结果。清除聊天记录。再次上传图片并将以下文本发送到聊天界面：

```
You will generate the website GUI template for the homepage of the e-commerce website.
Instructions:
1. Use the provided image to extract the layout, the sections, and the e-commerce products names and prices
2. Use html and bootstrap as output format
3. Add placeholders for products images
```

复制新的 HTML，导航回 **Visual Studio Code** 并用新 HTML 替换旧 HT​​ML。注意到任何差异了吗？请随意根据您希望实现的最终设计调整代码模板。

恭喜！您现在已经完成了实验的第三部分也是最后一部分，并且您了解了如何与多模式模型交互。单击下一步结束实验。
