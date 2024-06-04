# 第二部分 - 图像生成

欢迎参加本次研讨会的第二部分，我们将与文本到图像模型 DALL-E 3 进行交互。首先单击 **Images** 游乐场，然后从部署下拉菜单中选择 **dall-e-3**。

## 创建我们的第一幅图像

> [!TIP]
> 什么是 DALL-E 3？DALL-E 3 是一种基于神经网络的模型，可以从**自然语言输入**生成图形数据。更简单地说，您可以为 DALL-E 3 提供**描述**，它可以生成合适的图像。

让我们从生成图像开始，在描述框中输入基本提示，然后单击生成：

```A corgi practicing karate```


这将生成类似以下内容：

![Image of Corgi](./Images/A%20corgi%20practicing%20karate.png)

DALL-E 3 生成的图像是原创的；它们不是从精选图像目录中检索的。换句话说，DALL-E 3 不是用于查找合适图像的搜索系统 - 它是一个人工智能 (AI) 模型，它根据训练数据生成新图像。

### 具体

详细信息可使响应更准确。与文本生成类似，图像生成模型从您要生成的内容的详细描述中受益匪浅。

例如，输入以下提示：


```An elephant on a skateboard```


然后选择**Generate***并查看生成的图像。

现在，让我们通过在描述中添加更多详细信息来修改提示：


```A purple elephant on a skateboard performing an ollie, in the style of Picasso```


再次选择**Generate**并比较结果。

![Image of an elephant riding a skateboard](./Images/An%20elephant%20on%20a%20skateboard.png) ![Image of a purple elephant riding a skateboard in the style of Pablo Picasso](./Images/A%20purple%20elephant%20on%20a%20skateboard%20performing%20an%20olley,%20in%20the%20style%20of%20of%20Picasso.png)

### 最佳实践

要使用 DALL-E 3 创建有效且准确的图像，请遵循以下最佳实践：

1. **清晰且描述性强的提示**：编写清晰且详细的文本提示。您的描述越具体，DALL-E 3 生成符合您要求的图像的可能性就越大。包括主题、动作、环境、风格和任何重要细节等属性。

1. **使用形容词**：使用形容词和副词来描述您希望图像传达的品质、情感和特征。这有助于改进生成的图像以更好地匹配您的愿景。

1. **平衡细节与简单性**：虽然细节很重要，但过于复杂或矛盾的提示会让 AI 感到困惑，从而导致意想不到的结果。力求达到平衡，使您的描述提供足够的背景信息，而不会过于复杂。

1. **尝试不同的风格**：如果您希望图像具有特定的美感，请指定艺术风格或影响。例如，您可以要求提供梵高风格或未来概念艺术的图像。

1. **迭代方法**：通常，生成的第一张图像可能并不完美。将其用作起点，并根据输出迭代优化您的提示，以更接近您想要的结果。

1. **长宽比和构图**：如果您对图像的构图或长宽比有偏好，请将其包含在您的提示中。例如，您可能会要求横向图像或主体偏离中心的肖像。

1. **文化和背景参考**：如果合适，请包括文化或历史参考，以提供可帮助指导图像生成过程的额外背景。

1. **道德考虑**：注意提示的道德影响。避免创建令人反感、延续刻板印象或侵犯版权的图像。

1. **测试和学习**：尝试不同的提示，以了解 DALL-E 3 如何解释各种描述。这个学习过程可以帮助您随着时间的推移提高提示的准确性。

1. **遵循指南**：创建提示时，请遵守 OpenAI 的用例政策和内容指南。避免请求 OpenAI 内容政策不允许的图像。

## 网站目录创建

在本次研讨会中，我们将利用 DALL-E 3 的功能为 *Contoso Outdoor Company* 电子商务网站创建商品目录。

让我们从创建帐篷图像开始

> [!NOTE]
>提供的帐篷有 TrailMaster X4 帐篷、Alpine Explorer 帐篷和 SkyView 2 人帐篷。

要生成这些帐篷，请尝试这些提示的变体（发挥创意并根据需要进行调整！）：

```A simple brown tent made out of polyester```



```A robust, 8-person tent set up in the middle of an autumn forest```



```A small tent in the middle of a storm```


![Image of a brown tent](./Images/A%20simple%20brown%20tent%20made%20out%20of%20polyester.png) ![Image of a tent in an autumn forest](./Images/A%20robust,%208-person%20tent%20set%20up%20in%20the%20middle%20of%20an%20autumn%20forest.png) ![Image of a tent caught in the middle of a storm](./Images/A%20small%20tent%20in%20the%20middle%20of%20a%20storm.png)

接下来，让我们尝试生成背包。和以前一样，您可以随意调整提示并发挥创意！

> [!NOTE]
> 提供的背包有 Adventurer Pro 背包、SummitClimber 背包和 TrailLite Daypack。


```A compact hiking backpack in vibrant red color```



```A large, 70-liter backpacking pack fully loaded with camping gear```



```A small, realistic lightweight daypack```


![Image of a compact red hiking backpack](./Images/A%20compact%20hiking%20backpack%20in%20vibrant%20red%20color.png) ![Image of a large fully-loaded backpack for camping](./Images/A%20large,%2070-liter%20backpacking%20pack%20fully%20loaded%20with%20camping%20gear.png) ![Image of a small daypack](./Images/A%20small,%20realistic%20lightweight%20daypack.png)

最后，让我们为远足服装生成图像。

> [!NOTE]
> 库存中列出的远足服装包括 Summit Breeze 夹克、TrailBlaze 远足裤和 RainGuard 远足夹克。

```A waterproof, breathable rain jacket in bright yellow```

```A pair of rugged, cargo hiking pants in olive green```

```A down-filled, insulated winter jacket in deep blue```

![Image of a yellow rainjacket](./Images/A%20waterproof,%20breathable%20rain%20jacket%20in%20bright%20yellow.png) ![Image of a pair of olive green cargo pants](./Images/A%20pair%20of%20rugged,%20cargo%20hiking%20pants%20in%20olive%20green.png) ![Image of an insulated winter jacket](./Images/A%20down-filled,%20insulated%20winter%20jacket%20in%20deep%20blue.png)

## 高级提示

现在我们已经看到了一些基本的提示，我们不妨尝试一些新的东西？首先，让我们导航回**Chat Playground**。

>[!alert] 确保系统消息为空。如果需要，您只需单击**Reset to Default**即可。

我们现在将尝试根据 GPT-4 Turbo 生成的提示生成图像。

1. 为此，我们将使用我们想要为其创建图像的产品的详细描述：

```
Generate a prompt for DALL-E 3 from this product description:
The TrailMaster X4 Tent by OutdoorLiving offers adventurers a robust shelter for their outdoor excursions. Priced at $250, this polyester tent stands out with its easy-to-follow setup instructions and freestanding design, allowing for effortless relocation. The spacious interior comfortably houses multiple campers and their gear, while the 6-foot peak height ensures ample headroom. Designed to perform in a variety of conditions, the tent comes equipped with water-resistant construction and a 2000mm rated rainfly, ensuring dryness during light rain showers. The mesh panels promote airflow, double as insect protection, and along with the rainfly, provide added weatherproofing.

Beyond its practical features, the TrailMaster X4 Tent is designed with convenience in mind. It features two doors for easy access, interior pockets to help organize small items, and reflective guy lines for increased visibility at night. The tent's 80 square feet of floor area offers enough space for a comfortable camping experience. Additionally, the tent includes aluminum stakes, a gear loft for extra storage, and a carry bag for transport and storage. The green color of the tent blends seamlessly into natural settings, and its robust aluminum poles ensure a stable structure.

The TrailMaster X4 Tent is backed by a 2-year limited warranty and supported by a comprehensive user guide that covers setup, takedown, care, and maintenance, ensuring your investment is well-protected. With its combination of durability, practicality, and comfort, this tent is praised in customer reviews for its spaciousness and weather resistance. Whether you're a weekend warrior or a seasoned camper, the TrailMaster X4 Tent is designed to enhance your outdoor living experience.
```

2. 收到回复后，点击回复顶部的三个点，然后点击**Copy response to clipboard**。

![Image of copying option](./Images/ai-studio-copy-response.png)

3. 导航回 Images playground

4. **确保在 Deployments 下选择了 'dall-e-3'**，并将生成的提示粘贴到 **Prompt Box**。

5. 单击 **Generate**，并注意图像的详细程度。

恭喜！您现在已经完成了实验的第二部分，并为 Contoso Outdoors Company 电子商务网站生成了必要的图像资产。
