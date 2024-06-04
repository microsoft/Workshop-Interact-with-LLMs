# 第一部分 – 文本生成

> [!TIP]
> 什么是提示工程？

> 提示工程是自然语言处理 (NLP) 中的一个概念，涉及在输入中**嵌入任务描述**以**提示模型**输出**所需的结果**。

欢迎参加本 Workshop的第一部分，我们将与 GPT-4 Turbo 模型交互以生成文本。

## 初探提示工程

让我们从几个提示开始，并使用聊天界面并观察响应。

这里有一些示例可供尝试，但请发挥自己的提示创意，看看会发生什么！


### 网站副本和对话历史记录

```
Suggest a tagline for the website landing page of an e-commerce for outdoor clothing and equipment called Contoso Outdoor Company.
```

无需清除聊天记录，现在尝试以下提示：

```
Generate website copy for the homepage of the e-commerce website.
```

请注意，即使我们没有再次指定公司名称或业务，该模型也会为 *Contoso Outdoor Company* 网站提供副本。这是因为在后台，模型被赋予了 **整个对话历史记录** 作为上下文，而不仅仅是最新提示。如果用户离开并返回，AI 模型无法学习并且没有以前的交互记忆，但应用程序正在使用提示工程来添加此“记忆”。

> [!NOTE]
> 您可以通过进入 **参数** 选项卡来控制上下文窗口大小，即模型将视为上下文的先前交互的数量（默认值为 10）。

### 总结和关键实体提取

我们从上一步得到的最终副本已经是一个很好的起点，但对于着陆页来说可能太长了。让我们尝试获取它的一个较短版本。

文本总结是大型语言模型 (LLM) 的一项众所周知的功能。它为较大的文本创建简短的摘要。

> [!TIP]
> 要进行总结，您可以在提示中添加 tl;dr（“too long; didn't read”），后跟要总结的文本。

此外，您还可以指示您的 LLM 从文本中提取关键信息。在我们的场景中，这对于获取 **SEO 优化** 的关键字很有用。尝试以下提示来总结之前的副本，然后提取有用的数据。

```
1. tl;dr
2. Extract company name, categories of products and business unique values from the long description above.
```

## 高级提示

>[!alert] 在继续下一部分之前，请单击**Clear Chat**按钮以清除消息历史记录。

### 零样本学习

LLM 经过大量数据的训练，它们可能能够在很少的提示下执行某些任务。这被称为**零样本学习**。例如​​，让我们要求模型生成产品名称列表并对其进行分类：

```
Create a list of 10 product names the Contoso Outdoor shop might sell, include the type of item.
```

>[!alert] 在继续下一部分之前，请单击**Clear Chat**按钮以清除消息历史记录。

### 少样本学习

如果零样本学习无法满足您的示例和更复杂的任务，**少样本提示**可以提供示例，更好地引导模型实现预期结果。示例清楚地展示了我们希望模型如何运作。以下是用于对产品进行分类的少样本学习提示的示例。

```
Create a list of 10 product names the Contoso Outdoor shop might sell, include the type of item.

Examples:  
RidgeRunner Pro Trekking Poles: EQUIPMENT  
SummitShield 3-Season Tent: EQUIPMENT  
CascadeTech StormProof Jacket: APPAREL  
TerraFirm 40L Daypack: EQUIPMENT  
AlpineGlow Solar Lantern: EQUIPMENT
```

### 思维链提示

>[!alert] 在继续下一部分之前，请单击**Clear Chat**按钮以清除消息历史记录。

与 LLMs 交流时，一个有用的技巧是想象你正在与一名未经培训的实习生交谈。因此，你能提供的有关要执行的任务的详细信息越多，你得到的结果就越好。具体来说，一个有用的策略是将任务分解成更小的部分，并为每个部分提供提示。让我们在网站副本生成任务中尝试一下。


```
You will generate the website copy for the homepage of the Contoso Outdoor Company e-commerce website.
Instructions:
- Write a short welcome message for the homepage, specifying the company name and the main value proposition.
- Write a brief description of the business, including the categories of products offered.
- Write a short description for each of the following product categories: tents, backpacks, hiking clothing, sleeping bags.
```

另一种选择是使用一种称为**思维链**的技术，其中 LLM 负责将任务分解为更小的步骤。LLM 使用其对世界的了解和推理能力。然后，LLM 生成一系列思维，以解决任务。

再次清除 Playground 聊天，然后输入下面的用户提示，以查看“思维链提示”的实际效果：

```
Generate the website copy for the homepage of the Contoso Outdoor Company e-commerce website.
Take a step-by-step approach in your response, include a welcome message, a brief description of the business, and a description of the product categories offered (tents, backpacks, hiking clothing, sleeping bags). Also, give reasoning before sharing the final answer in the below format: ANSWER is: <website copy>.
```

## 系统消息和新增知识

>[!alert] 在继续下一部分之前，请单击 **清除聊天** 按钮以清除消息历史记录。

### 系统消息

> [!TIP]
> 什么是 **系统消息**？系统消息用于在对话开始时向模型传达指令或提供背景信息。它以与用户消息不同的格式显示，帮助模型了解其在对话中的角色。系统消息通常指导模型的行为、设定基调或指定模型的期望输出。通过有效利用系统消息，用户可以引导模型生成更准确、更相关的响应。

在系统消息字段中插入以下文本，然后单击“Apply changes”。

```
## Task
You are a web copywriter for the Contoso Outdoor Company e-commerce website. Your goal is to generate the website copy for the homepage. 
Your answer should be brief and engaging. Always use a friendly and professional tone of voice.
Always show the word CONTOSO in capital letters.

## Safety
In the copy you write always stick to the subject of the company and the products it offers. Avoid any irrelevant information and controversial opinions.
```

请注意，我们为模型提供了**明确的任务**、**语气**和**安全措施**以供遵循。您的模型就像任何用于业务的技术一样，就像您的品牌一样。如果您希望它具有与您在整个业务中灌输的行为准则相同的方法和道德规范，它也应该包含在您的 AI 解决方案中。在系统消息中设置围绕语气的部分有助于设置适合您用例的响应类型。

系统消息中提供的文本由模型专门处理，旨在对模型的响应产生比用户消息文本或提示中提供的其他上下文更大的影响。此外，即使您清除聊天历史记录，它也会保留在聊天中的所有交互中。

要查看模型的行为如何随着添加的上下文而变化，请尝试以下提示：

```
Write a brief description of the business, including the categories of products offered.
```

您将看到模型不仅响应了请求的信息，而且还准确地执行了任务，例如用大写字母写出 CONTOSO。为了更进一步，我们可以测试**安全措施**：

```
What are your thoughts on the upcoming election?
```

模型将避免回答这个问题（因为这与公司无关并且可能被视为有争议），并坚持公司及其产品的主题。

### 有根据的提示

>[!alert] 确保在继续此部分之前**Clear Chat**。

在我们迄今为止生成的网站副本中，该模型在发明业务价值主张和产品供应方面很有创意。然而，在现实世界中，我们希望模型生成的文本基于现实并反映实际业务。为了实现这一点，我们可以使用一种称为**检索增强生成 (RAG)** 的技术。该技术涉及为模型提供一组有关业务的事实或信息，然后模型可以使用这些信息来生成更准确、更相关的文本。

> [!NOTE]
> **检索增强生成 (RAG)** 是一种 AI 技术，它将语言模型与搜索系统相结合，以提供更准确、更详细的信息。在 RAG 模式中，系统通常从数据库中检索相关信息，然后使用它来帮助生成更明智、更符合上下文的文本响应。为了完成本实验，我们将通过在提示中向模型提供一组有关业务的事实来模拟检索过程。

始终可以通过系统消息提供附加知识。因此，让我们添加到当前系统消息中。在现有系统提示的末尾插入以下信息，然后单击**Apply changes**。

```
## Business Information
Contoso Outdoor Company is an e-commerce business that specializes in outdoor clothing and equipment. The company offers a wide range of products, including tents, backpacks, hiking clothing, and sleeping bags. The company's main value proposition is to provide high-quality outdoor gear for every level of outdoor enthusiast at affordable prices.

Products offered:
1. Tents: 
    - TrailMaster X4 Tent: Crafted from durable polyester, this tent boasts a spacious interior perfect for four occupants. It ensures your dryness under drizzly skies thanks to its water-resistant construction, and the accompanying rainfly adds an extra layer of weather protection.
    - Alpine Explorer Tent: This robust, 8-person, 3-season marvel is from the responsible hands of the AlpineGear brand. Promising an enviable setup that is as straightforward as counting sheep, your camping experience is transformed into a breezy pastime.
    - SkyView 2-Person Tent: This tent offers a spacious interior that houses two people comfortably, with room to spare. Crafted from durable waterproof materials to shield you from the elements, it is the fortress you need in the wild. 

2. Backpacks:
    - Adventurer Pro Backpack: Uniquely designed with ergonomic comfort in mind, this backpack ensures a steadfast journey no matter the mileage. It boasts a generous 40L capacity wrapped up in durable nylon fabric ensuring its long-lasting performance on even the most rugged pursuits. 
    - SummitClimber Backpack: your reliable partner for every exhilarating journey. With a generous 60-liter capacity and multiple compartments and pockets, packing is a breeze. Every feature points to comfort and convenience; the ergonomic design and adjustable hip belt ensure a pleasantly personalized fit, while padded shoulder straps protect you from the burden of carrying. 
    - TrailLite Daypack: Built for comfort and efficiency, this lightweight and durable backpack offers a spacious main compartment, multiple pockets, and organization-friendly features all in one sleek package. 

3. Hiking Clothing:
    - Summit Breeze Jacket: This lightweight jacket is your perfect companion for outdoor adventures. Sporting a trail-ready, windproof design and a water-resistant fabric, it's ready to withstand any weather. 
    - TrailBlaze Hiking Pants: Crafted from high-quality nylon fabric, these dapper troopers are lightweight and fast-drying, with a water-resistant armor that laughs off light rain. Their breathable design whisks away sweat while their articulated knees grant you the flexibility of a mountain goat.
    - RainGuard Hiking Jacket: the ultimate solution for weatherproof comfort during your outdoor undertakings! Designed with waterproof, breathable fabric, this jacket promises an outdoor experience that's as dry as it is comfortable.
```

要查看模型的行为如何随着添加的上下文而变化，请尝试以下提示：

```
Write a short description for each of the following product categories: tents, backpacks, hiking clothing.
```

恭喜，您已完成实验的第一部分！您已经学习了如何使用提示工程通过语言模型生成文本。在实验的下一部分中，您将学习如何使用该模型生成图像资源。
