# Part 1 - Text Generation

> [!TIP]
> What is prompt engineering?
> Prompt engineering is a concept in Natural Language Processing (NLP) that involves **embedding descriptions of tasks** in input to **prompt the model** to output the **desired results**.

Welcome to part 1 of this workshop, where we'll be interacting with GPT4-turbo model to generate text. Before starting, make sure your playground is configured as follow:
- Mode: Chat
- Deployment: gpt-4-turbo

## Basic prompting

Let's start with a few prompts and observe the response using the chat interface.

Here are some examples to try, but get creative with your own prompts and see what happens!

> [!NOTE]
> Open the Notepad app and copy the model's responses you get at each step. You'll need them in a later stage.

### Website copy and conversation history

```
Suggest a tagline for the website landing page of an e-commerce for outdoor clothing and equipment called Contoso Outdoor Company.
```

Without clearing the chat history, try now the following prompt:

```
Generate website copy for the homepage of the e-commerce website.s
```

Note that the model is providing a copy for the *Contoso Outdoor Company* website, even if we didn't specify again the company name or business. This is because under the hoods the model is given the **whole conversation history** as context, not just the latest prompt. An AI model cannot learn and has no memory of previous interactions if the user leaves and comes back but the application is using prompt engineering to add this 'memory'. 

To verify that, try clearing the chat history, enter the prompt again and check how the model's response changes.

> [!NOTE]
> In the Azure AI Studio Playground there's also a **Session Settings** option that allows you to control the context window size, which is the number of previous interactions that the model will consider as context (default is 10).

### Summarization and key entities extraction

The resulting copy we have got from the previous step is already a good starting point, but it might be too long for a landing page. Let's try to get a shorter version of it.

Text summarization is a well known capability of LLMs - it creates a short summary of a larger piece of text. Add tl;dr (for "too long; didn't read") to gain a summary of the copy generated in the previous step.

```
tl;dr
<AI Generated Website Copy>
```

Similarly, you can instruct your LLM to extract key information from a text. In our scenario, this is useful to get keywords for **SEO optimization**. Try the prompt below, by replacing `<AI Generated Copy Summary>` with the text generated in the previous step.

```
Extract company name, categories of products and business unique values from the description below.
<AI Generated Copy Summary>
```

## Advanced prompting

### Zero-shot learning

LLMs are trained on such large amounts of data they may be able to perform some tasks with very little prompting. This is known as **zero-shot learning**. For example, now that we have the AI generated website copy, we can ask the model to translate it into a different language to enable localization, using the simple prompt below.

```
Translate the website copy into French.
English: <AI Generated Website Copy>
French:
```

### Few-shot learning

If zero-shot learning is failing for your examples and more complex tasks, **few shot prompting** can provide examples that can better steer the model to the desired outcomes. Examples show the model cleanly how we want it to operate. Here's an example of a few-shot learning prompt for translation.

```
English: Welcome to Contoso Outdoor Company, your one-stop shop for all your outdoor gear and equipment needs.
French: Bienvenue chez Contoso Outdoor Company, votre guichet unique pour tous vos besoins en équipement et matériel de plein air.
English: We offer a wide range of products, from camping gear to hiking equipment.
French: Nous proposons une large gamme de produits, de l'équipement de camping à l'équipement de randonnée.
English:
```

### Chain of thought prompting

When interacting with LLMs, a useful tip is to imagine that you are speaking to an untrained intern. So the more details you can provide about the task to be performed, the better the results you will get. In particular, a useful strategy is to break down the task into smaller parts and provide a prompt for each part. Let's try this with the website copy generation task.
Before you start, clear the chat history to avoid any context from previous interactions.

```
You will generate the website copy for the homepage of the Contoso Outdoor Company e-commerce website.
Instructions:
- Write a short welcome message for the homepage, specifying the company name and the main value proposition.
- Write a brief description of the business, including the categories of products offered.
- Write a short description for each of the following product categories: tents, backpacks, hiking clothing, sleeping bags.
```

Another option is using a technique - called **chain of thought** - where the LLM is responsible for breaking the task down into smaller steps. The LLM uses its knowledge of the world and its ability to reason. The LLM then generates a chain of thoughts that leads to the solution of the task.
Clear the playground chat again and then enter the user prompt below to see 'Chain of thought prompting' in action:

```
Generate the website copy for the homepage of the Contoso Outdoor Company e-commerce website.
Take a step-by-step approach in your response, include a welcome message, a brief description of the business, and a description of the product categories offered (tents, backpacks, hiking clothing, sleeping bags). Also, give reasoning before sharing the final answer in the below format: ANSWER is: <website copy>.
```

## System message and added knowledge

### System message

> [!TIP]
> What is the **system message**? The system message is used to communicate instructions or provide context to the model at the beginning of a conversation. It is displayed in a different format compared to user messages, helping the model understand its role in the conversation. The system message typically guides the model's behavior, sets the tone, or specifies desired output from the model. By utilizing the system message effectively, users can steer the model towards generating more accurate and relevant responses.

In the System message field insert the text below, then click "Apply changes".

```
## Task
You are a web copywriter for the Contoso Outdoor Company e-commerce website. Your goal is to generate the website copy for the homepage. 
Your answer should be brief and engaging. Always use a friendly and professional tone of voice.

## Safety
In the copies you write always stick to the subject of the company and the products it offers. Avoid any irrelevant information and controversial opinions.
```

Observe that we have provided the model with a **clear task**, a **tone of voice**, and **safety measures** to follow. Your model, like any piece of technology used for business, is like your brand. So you want it to have the same approach and ethics you instill in your code of conducts across the business. Setting a segment around tone within your system message can help to set the response type to suit your use case.

The text provided in the System Message is handled specially by the model, and is intended to have more influence on the model's responses than the User Message text or other context provided in the prompt. Also, it is persisted across all the interactions in the chat, even if you clear the chat history.

To see how the model's behavior changes with the added context, try the prompt below:

```
Write a brief description of the business, including the categories of products offered.
```

### Grounded prompting

In the copies we have generated so far, the model has been creative in inventing a business value proposition and product offering. However, in real-world scenarios, we want the model to generate text that is grounded in reality and reflects the actual business. To achieve this, we can use a technique called **Retrieval Augmented Generation**. This technique involves providing the model with a set of facts or information about the business, which the model can then use to generate more accurate and relevant text. 

> [!NOTE]
> **Retrieval-Augmented Generation** (RAG) is an AI technique that combines a language model with a search system to provide more accurate and detailed information. In a RAG pattern, the system usually retrieves relevant information from a database and then uses it to help generate more informed and contextually accurate text responses. For the sake of this lab, we will simulate the retrieval process by providing the model with a set of facts about the business in the prompt.

Added knowledge can be provided always through the System message. So, let's add to the current System message the information below, and then click "Apply changes".

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

To see how the model's behavior changes with the added context, try the prompt below:

```
Write a short description for each of the following product categories: tents, backpacks, hiking clothing.
```
Congratulations, you have completed the first part of the lab! You have learned how to use prompt engineering to generate text using a language model. In the next part of the lab, you will learn how to use the model to generate image assets.
