---
title: "提示设计策略  |  Gemini API"
source: "https://ai.google.dev/gemini-api/docs/prompting-strategies?hl=zh-cn"
author:
published:
created: 2026-04-12
description:
tags:
  - "clippings"
---
不妨试用全新高速且经济实惠的 [Veo 3.1 Lite](https://ai.google.dev/gemini-api/docs/models/veo-3.1-lite-generate-preview?hl=zh-cn) 模型，大规模生成视频。

提示设计是指创建提示（即自然语言请求）的过程，这些提示将用来从语言模型获得准确、高画质的回答。

本页面介绍了一些基本概念、策略和最佳实践，可帮助您开始设计提示，以便充分利用 Gemini AI 模型。

## 针对特定主题的提示指南

想要了解更具体的提示策略？不妨查看我们的其他提示指南：

- [使用媒体文件进行提示](https://ai.google.dev/gemini-api/docs/files?hl=zh-cn#prompt-guide)
- 使用 [Imagen](https://ai.google.dev/gemini-api/docs/imagen?hl=zh-cn#imagen-prompt-guide) 和 [Gemini 原生图片生成](https://ai.google.dev/gemini-api/docs/image-generation?hl=zh-cn#prompt-guide) 功能生成图片的提示
- [视频生成提示](https://ai.google.dev/gemini-api/docs/video?hl=zh-cn#prompt-guide)

您可以在 [提示库](https://ai.google.dev/gemini-api/prompts?hl=zh-cn) 中找到其他示例提示，这些提示旨在以互动方式展示本指南中分享的许多概念。

## 清晰具体的说明

自定义模型行为的一种有效且高效的方法是向模型提供清晰具体的指令。指令可以采用问题、分步任务的形式，也可以很复杂，例如反映用户的体验和思维模式。

### 输入

输入是提示中您希望模型为其提供回答的必需文本。输入可以是模型回答的问题（问题输入）、模型执行的任务（任务输入）、模型操作的实体（实体输入），或模型完成或继续的部分输入（补全输入）。

| **输入类型** | **提示** | **生成的输出** |
| --- | --- | --- |
| Question | ``` What's a good name for a flower shop that specializes in selling bouquets of dried flowers? Create a list of 5 options with just the names. ``` | ``` Here are 5 names for a flower shop specializing in dried flowers:  1. Everlasting Blooms 2. Dried & Delightful 3. The Petal Preserve 4. Whispers of Wildflowers 5. Forever Blooms ``` |
| 任务 | ``` Give me a simple list of just the things that I must bring on a camping trip. The list should have 5 items. ``` | ``` 1. **Tent:** Your shelter from the elements. 2. **Sleeping Bag:** Stay warm and comfortable. 3. **Sleeping Pad:** Insulation and cushioning for a good night's sleep. 4. **Headlamp or Flashlight:** Light for nighttime activities. 5. **First Aid Kit:** Be prepared for minor injuries. ``` |
| 实体 | ``` Classify the following items as [large, small]: Elephant Mouse Snail ``` | ``` Here's the classification:  * **Elephant:** Large * **Mouse:** Small * **Snail:** Small ``` |

#### 部分输入内容补全

生成式语言模型的工作方式类似于高级自动补全工具。当您提供部分内容时，模型可以提供剩余的内容或者它认为是该内容的延续内容来作为回答。如果您添加了任何示例或上下文，模型可以参考这些示例或上下文。

以下示例提供了包含指令和实体输入的提示：

```
For the given order, return a JSON object that has the fields cheeseburger, hamburger, fries, or
drink, with the value being the quantity.

Order: A burger and a drink.
```
```
{
  "cheeseburger": 0,
  "hamburger": 1,
  "fries": 0,
  "drink": 1
}
```

虽然模型按照提示提供了回答，但以自然语言编写指令有时可能并不容易，并且模型需要解释许多内容。例如，餐馆菜单可能包含许多菜品。为了减小 JSON 回答的大小，建议您省略没有点的菜品。在这种情况下，您可以提供一个示例和回答前缀，让模型来补全它：

```
Valid fields are cheeseburger, hamburger, fries, and drink.
Order: Give me a cheeseburger and fries
Output:
\`\`\`
{
  "cheeseburger": 1,
  "fries": 1
}
\`\`\`
Order: I want two burgers, a drink, and fries.
Output:
```
```
\`\`\`
{
  "hamburger": 2,
  "drink": 1,
  "fries": 1
}
\`\`\`
```

可以看到，输出中排除了“芝士汉堡”，因为点餐中没有芝士汉堡。

虽然您可以使用提示指定简单 JSON 响应对象的格式，但我们建议您在为响应指定更复杂的 JSON 架构时，使用 Gemini API 的 [结构化输出](https://ai.google.dev/gemini-api/docs/structured-output?hl=zh-cn) 功能。

### 限制条件

指定有关读取提示或生成回答的任何限制条件。您可以告诉模型要做什么和不应该做什么。例如，您可以在提示中指定一个限制条件，以限制摘要长度：

```
Summarize this text in one sentence:
Text: A quantum computer exploits quantum mechanical phenomena to perform calculations exponentially
faster than any modern traditional computer. At very tiny scales, physical matter acts as both
particles and as waves, and quantum computing uses specialized hardware to leverage this behavior.
The operating principles of quantum devices is beyond the scope of classical physics. When deployed
at scale, quantum computers could be used in a wide variety of applications such as: in
cybersecurity to break existing encryption methods while helping researchers create new ones, in
meteorology to develop better weather forecasting etc. However, the current state of the art quantum
computers are still largely experimental and impractical.
```
```
Exploiting quantum mechanical phenomena, quantum computers can perform calculations exponentially faster than traditional computers for potential applications like cybersecurity and meteorology, although they are currently largely experimental and impractical.
```

### 回答格式

您可以提供指定回答格式的说明。例如，您可以要求将回答格式设置为表格、项目符号列表、电梯间推销、关键字、句子或段落。以下系统指令会指示模型在回答时更具对话性：

```
All questions should be answered comprehensively with details, unless the user requests a concise response specifically.
```
```
What is a smart way to make a business that sells DVD's in 2026?
```
```
Starting a business selling DVDs in 2026 presents significant challenges due to the overwhelming dominance of digital streaming and on-demand services; a "smart" approach would therefore require a highly specialized niche, a strong value proposition beyond just the disc, and likely a focus on community or collector markets rather than mainstream consumption.

Here's a breakdown of what a smart DVD business in 2026 would likely entail:

1. Extreme Niche Specialization: You cannot compete with streaming libraries. Your business must focus on what digital doesn't offer easily or at all. This could include:

    * Out-of-Print & Rare Titles: Sourcing films or TV shows that have never been released digitally or are currently unavailable on major streaming platforms.
    ....
```

#### 使用补全策略设置回答格式

[补全策略](#completion) 也有助于设置回答的格式。 以下示例提示模型创建论文大纲：

```
Create an outline for an essay about hummingbirds.
```
```
Here is a possible outline for an essay about hummingbirds:

I. Introduction
A. Hook: Start with a captivating fact or description about hummingbirds (e.g., their speed, iridescent colors, or tiny size).
B. Background: Briefly introduce hummingbirds – where they are found (Americas), their reputation as unique birds.
C. Thesis Statement: State the main point of the essay, which could be about the remarkable adaptations, behaviors, and ecological importance of hummingbirds.

II. Appearance and Identification
.....
```

提示没有指定大纲的格式，模型为您选择了格式。如需使模型以特定格式返回大纲，您可以添加表示大纲开头的文本，并让模型根据您起头的模式补全大纲。

```
Create an outline for an essay about hummingbirds.
I. Introduction
   *
```
```
Okay, here is an outline for an essay about hummingbirds, starting from the introduction you provided:

I. Introduction
* Hook: Start with a captivating fact or description about hummingbirds (e.g., their speed, iridescent colors, or tiny size).
* Background: Briefly introduce hummingbirds – where they are found (Americas), their reputation as unique birds, and their general characteristics.
* Thesis Statement: State the main point of the essay, focusing on the remarkable adaptations, behaviors, and ecological significance that make hummingbirds extraordinary.
.....
```

## 零样本提示与少样本提示

您可以在提示中添加示例，以向模型示范想要的结果。模型会尝试识别示例中的模式和关系，并在生成回答时应用它们。包含少量示例的提示称为少样本提示，而不提供示例的提示称为零样本提示。少样本提示通常用于规定模型回答的格式、措辞、范围界定或一般模式。使用具体而多样的示例来帮助模型缩小其重点并生成更准确的结果。

我们建议始终在提示中包含少样本示例。不含少样本示例的提示可能效果不大。事实上，如果您的示例足够清晰地显示当前任务，则您可以从提示中移除指令。

以下零样本提示要求模型选择最佳解释。

```
Please choose the best explanation to the question:

Question: How is snow formed?
Explanation1: Snow is formed when water vapor in the air freezes into ice
crystals in the atmosphere, which can combine and grow into snowflakes as they
fall through the atmosphere and accumulate on the ground.
Explanation2: Water vapor freezes into ice crystals forming snow.
Answer:
```
```
Explanation1 is the better explanation because it provides more detail on the
process, including how ice crystals combine and grow into snowflakes as they
fall through the atmosphere.
```

如果您的用例要求模型生成简洁的回答，您可以在提示中添加偏好简洁回答的示例。

以下提示提供了两个偏好较短解释的示例。在回答中，您可以看到这些示例引导模型选择较短的解释 (`Explanation2`)，而不是像之前那样较长的解释 (`Explanation1`)。

```
Below are some examples showing a question, explanation, and answer format:

Question: Why is the sky blue?
Explanation1: The sky appears blue because of Rayleigh scattering, which causes
shorter blue wavelengths of light to be scattered more easily than longer red
wavelengths, making the sky look blue.
Explanation2: Due to Rayleigh scattering effect.
Answer: Explanation2

Question: What is the cause of earthquakes?
Explanation1: Sudden release of energy in the Earth's crust.
Explanation2: Earthquakes happen when tectonic plates suddenly slip or break
apart, causing a release of energy that creates seismic waves that can shake the
ground and cause damage.
Answer: Explanation1

Now, Answer the following question given the example formats above:

Question: How is snow formed?
Explanation1: Snow is formed when water vapor in the air freezes into ice
crystals in the atmosphere, which can combine and grow into snowflakes as they
fall through the atmosphere and accumulate on the ground.
Explanation2: Water vapor freezes into ice crystals forming snow.
Answer:
```
```
Answer: Explanation2
```

### 最佳示例数量

Gemini 等模型通常可以通过少量示例来学习模式，但您可能需要进行多次实验，以找到可产生最佳结果的提示中提供的示例数量。但是，如果您添加太多示例，模型的回答可能会与示例 [过拟合](https://developers.google.com/machine-learning/glossary?hl=zh-cn#overfitting) 。

### 采用风格一致的内容形式

确保少样本示例的结构和格式相同，以避免回答具有不需要的格式。在提示中添加少样本示例的主要目标之一是向模型展示回答格式。因此，必须确保在所有示例中使用一致的格式，尤其是注意 XML 标记、空格、换行符和示例分隔符。

## 添加上下文

您可以在提示中添加模型解决问题所需的指令和信息，而不是假设模型具备所有必要信息。这些上下文信息可帮助模型了解您要求其执行的操作的限制和详细信息。

以下示例要求模型提供路由器的问题排查指导：

```
What should I do to fix my disconnected wifi? The light on my Google
Wifi router is yellow and blinking slowly.
```
```
A yellow blinking light on your Google Wifi router usually indicates a problem
  with the internet connection. Here are some steps to troubleshoot and fix the
  issue:
  1. Restart your router and modem:
    - Unplug your modem from the power outlet and wait for 30 seconds.
    - Plug your modem back in and wait for it to fully boot up.
    - Unplug your Google Wifi router and wait for 30 seconds.
    - Plug your Google Wifi router back in and wait for it to fully boot up.
.....
```

这个回答看起来是通用的问题排查信息，并非特定于路由器或 LED 指示灯的状态。

如需针对特定路由器自定义回答，您可以在提示中添加该路由器的问题排查指南作为上下文，供模型在回答时参考。

```
Answer the question using the text below. Respond with only the text provided.
Question: What should I do to fix my disconnected wifi? The light on my Google Wifi router is yellow and blinking slowly.

Text:
Color: Slowly pulsing yellow
What it means: There is a network error.
What to do:
Check that the Ethernet cable is connected to both your router and your modem and both devices are turned on. You might need to unplug and plug in each device again.

Color: Fast blinking yellow
What it means: You are holding down the reset button and are factory resetting this device.
What to do:
If you keep holding down the reset button, after about 12 seconds, the light will turn solid yellow. Once it is solid yellow, let go of the factory reset button.

Color: Solid yellow
What it means: Router is factory resetting.
What to do:
This can take up to 10 minutes. When it's done, the device will reset itself and start pulsing white, letting you know it's ready for setup.

Color: Solid red
What it means: Something is wrong.
What to do:
Critical failure. Factory reset the router. If the light stays red, contact Wifi customer support.
```
```
Check that the Ethernet cable is connected to both your router and your modem and both devices are turned on. You might need to unplug and plug in each device again.
```

## 将提示分解为各个组成部分

对于需要复杂提示的用例，您可以将内容细分为更简单的组成部分，以帮助模型管理这种复杂情况。

1. **细分指令** ：不要在一个提示中包含多条指令，而要为每条指令创建一个提示。您可以根据用户的输入选择要处理的提示。
2. **串联提示** ：对于涉及多个连续步骤的复杂任务，请将每个步骤设为一个提示，并将这些提示按顺序串联在一起。在这一连串的提示中，序列中一个提示的输出将成为下一个提示的输入。序列中最后一个提示的输出将是最终输出。
3. **汇总回答** ：汇总是指对数据的不同部分执行不同的并行任务，并汇总结果以生成最终输出。例如，您可以指示模型对数据的第一部分执行一项操作，对其余数据执行另一项操作并汇总结果。

## 对模型参数进行实验

您向模型发送的每次调用都包含控制模型如何生成回答的参数值。对于不同的参数值，模型会生成不同的结果。因此请尝试不同的参数值，以获得任务的最佳值。不同模型的可用参数可能有所不同。最常见的参数如下：

1. **最大输出词元数** ：指定回答中可生成的词元数量上限。词元约为 4 个字符。100 个 token 大约对应 60-80 个单词。
2. **温度** ：温度可以控制 token 选择的随机性。温度 (temperature) 在生成回答期间用于采样，在应用 `topP` 和 `topK` 时会生成回答。较低的温度有利于需要更具确定性或更少开放性回答的提示，而较高的温度可以带来更具多样性或创造性的结果。温度为 0 表示确定性，即始终选择概率最高的回答。
3. **`topK`** ： `topK` 参数可更改模型选择输出 token 的方式。如果 `topK` 设为 1，表示所选 token 是模型词汇表的所有 token 中概率最高的 token（也称为贪心解码）。如果 `topK` 设为 3，则表示系统将从 3 个概率最高的 token（通过温度确定）中选择下一个 token。在每个词元选择步骤中，系统都会对概率最高的 `topK` 个词元进行采样。然后，系统会根据 `topP` 进一步过滤词元，并使用温度采样选择最终的词元。
4. **`topP`** ： `topP` 参数可更改模型选择输出 token 的方式。系统会按照概率从最高到最低的顺序选择 token，直到所选 token 的概率总和等于 `topP` 值。例如，如果词元 A、B 和 C 的概率分别为 0.3、0.2 和 0.1，并且 `topP` 值为 0.5，则模型将选择 A 或 B 作为下一个词元（通过温度确定），并会排除 C 作为候选词元。默认 `topP` 值为 0.95。
5. **`stop_sequences`** ：设置停止序列，告知模型停止生成内容。停止序列可以是任意字符序列。尽量避免使用可能会出现在生成内容中的字符序列。

## 提示迭代策略

提示设计有时需要进行几次迭代，然后才能稳定获得所需的回答。本部分提供了有关在迭代提示时可以尝试的一些做法的指导：

1. **使用不同的措辞** ：即使含义相同，在提示中使用不同的字词或措辞通常也会使模型生成不同的回答。如果您的提示无法产生预期结果，请尝试重新措辞。
	```
	Version 1:
	How do I bake a pie?
	Version 2:
	Suggest a recipe for a pie.
	Version 3:
	What's a good pie recipe?
	```
2. **改用类似任务** ：如果您无法让模型遵循您的任务指令，请尝试为其提供可实现相同结果的类似任务的指令。
	此提示指示模型使用预定义的类别对一本书进行分类：
	```
	Which category does The Odyssey belong to:
	thriller
	sci-fi
	mythology
	biography
	```
	```
	The Odyssey belongs to the category of **mythology**. 
	    Here's why:
	    * **Mythology:** The Odyssey tells the story of Odysseus, a hero from Greek mythology, and his
	    journey home after the Trojan War. It features gods, monsters, and supernatural events common to
	    Greek mythology.
	.....
	```
	回答正确，但模型超出了选项的范围。您还希望模型仅使用其中一个选项（而不是完整的句子）来回答。在这种情况下，您可以将指令改为单选题，并要求模型选择一个选项。
	```
	Multiple choice problem: Which of the following options describes the book The Odyssey?
	Options:
	thriller
	sci-fi
	mythology
	biography
	```
	```
	The correct answer is mythology.
	```
3. **更改提示内容的顺序** ：提示中内容的顺序有时会影响回答。请尝试更改内容顺序，看看对回答有何影响。
	```
	Version 1:
	[examples]
	[context]
	[input]
	Version 2:
	[input]
	[examples]
	[context]
	Version 3:
	[examples]
	[input]
	[context]
	```

## 后备响应

后备回答是当提示或回答触发安全过滤条件时模型返回的回答。后备回答的一个示例是“我无法提供帮助，因为我只是一个语言模型”。

如果模型给出后备回答，请尝试提高温度。

## 接地和代码执行

Gemini 能够使用工具来避免在可能生成错误回答的情况下出现幻觉。

[依托 Google 搜索进行接地](https://ai.google.dev/gemini-api/docs/google-search?hl=zh-cn) 可将 Gemini 模型与实时网络内容相关联，当模型可能需要了解冷门或最新事实时，应启用此功能。

Gemini 的 [代码执行工具](https://ai.google.dev/gemini-api/docs/code-execution?hl=zh-cn) 可让模型生成和运行 Python 代码，并且只要模型需要执行任何类型的算术、计数或计算，就应启用该工具。

## Gemini 3

[Gemini 3 模型](https://ai.google.dev/gemini-api/docs/models?hl=zh-cn#gemini-3) 专为高级推理和指令遵从而设计。它们最能理解直接、结构合理且清晰定义了任务和任何限制条件的提示。建议采用以下做法，以充分发挥 Gemini 3 的性能：

### 核心提示原则

- **用词要准确、直接** ：清晰简洁地说明您的目标。避免使用不必要或过于具有说服力的语言。
- **使用一致的结构** ：使用清晰的分隔符分隔提示的不同部分。XML 样式的标记（例如 `<context>` 、 `<task>` ）或 Markdown 标题都有效。选择一种格式，并在单个提示中始终使用该格式。
- **定义参数** ：明确说明任何模棱两可的术语或参数。
- **控制输出详细程度** ：默认情况下，Gemini 3 模型会提供直接而高效的回答。如果您需要更口语化或更详细的回答，必须在指令中明确提出要求。
- **连贯地处理多模态输入** ：使用文本、图片、音频或视频时，将它们视为同类输入。确保您的说明根据需要清楚地提及每种模态。
- **优先处理关键指令** ：将必要的行为限制、角色定义（角色设定）和输出格式要求放在系统指令中或用户提示的最开头。
- **长上下文的结构** ：提供大量上下文（例如文档、代码）时，请先提供所有上下文。将具体说明或问题放在提示的 *末尾* 。
- **锚定上下文** ：在提供大量数据后，使用清晰的过渡短语来连接上下文和您的查询，例如“根据上述信息…”

### Gemini 3 Flash 策略

- **当前日期准确性** ：在系统指令中添加以下子句，以帮助模型注意当前日期是 2026 年：
	```
	For time-sensitive user queries that require up-to-date information, you
	MUST follow the provided current time (date and year) when formulating
	search queries in tool calls. Remember it is 2026 this year.
	```
- **知识截点准确性** ：在系统指令中添加以下子句，让模型了解其知识截点：
	```
	Your knowledge cutoff date is January 2025.
	```
- **事实依据性能** ：在系统指令中添加以下子句（可根据需要进行修改），以提高模型根据所提供的上下文生成回答的能力：
	```
	You are a strictly grounded assistant limited to the information provided in
	the User Context. In your answers, rely **only** on the facts that are
	directly mentioned in that context. You must **not** access or utilize your
	own knowledge or common sense to answer. Do not assume or infer from the
	provided facts; simply report them exactly as they appear. Your answer must
	be factual and fully truthful to the provided text, leaving absolutely no
	room for speculation or interpretation. Treat the provided context as the
	absolute limit of truth; any facts or details that are not directly
	mentioned in the context must be considered **completely untruthful** and
	**completely unsupported**. If the exact answer is not explicitly written in
	the context, you must state that the information is not available.
	```

### 增强推理和规划能力

Gemini 2.5 和 3 系列模型会自动生成内部“思考”文本，以提升推理性能。因此，一般而言，无需在返回的回答中包含模型大纲、计划或详细推理步骤。对于需要大量推理的问题，简单的请求（例如“在回答之前认真思考”）可以提高性能，但会消耗额外的思考 token。

如需了解详情，请参阅 [Gemini 思维](https://ai.google.dev/gemini-api/docs/thinking?hl=zh-cn) 文档。

### 结构化提示示例

使用标记或 Markdown 有助于模型区分指令、上下文和任务。

**XML 示例** ：

```
<role>
You are a helpful assistant.
</role>

<constraints>
1. Be objective.
2. Cite sources.
</constraints>

<context>
[Insert User Input Here - The model knows this is data, not instructions]
</context>

<task>
[Insert the specific user request here]
</task>
```

**Markdown 示例** ：

```
# Identity
You are a senior solution architect.

# Constraints
- No external libraries allowed.
- Python 3.11+ syntax only.

# Output format
Return a single code block.
```

### 结合了最佳实践的模板示例

此模板涵盖了 Gemini 3 的提示核心原则。请务必根据您的具体使用场景进行迭代和修改。

**系统指令** ：

```
<role>
You are Gemini 3, a specialized assistant for [Insert Domain, e.g., Data Science].
You are precise, analytical, and persistent.
</role>

<instructions>
1. **Plan**: Analyze the task and create a step-by-step plan.
2. **Execute**: Carry out the plan.
3. **Validate**: Review your output against the user's task.
4. **Format**: Present the final answer in the requested structure.
</instructions>

<constraints>
- Verbosity: [Specify Low/Medium/High]
- Tone: [Specify Formal/Casual/Technical]
</constraints>

<output_format>
Structure your response as follows:
1. **Executive Summary**: [Short overview]
2. **Detailed Response**: [The main content]
</output_format>
```

**用户提示** ：

```
<context>
[Insert relevant documents, code snippets, or background info here]
</context>

<task>
[Insert specific user request here]
</task>

<final_instruction>
Remember to think step-by-step before answering.
</final_instruction>
```

## 智能体工作流

对于深度智能体工作流，通常需要提供具体指令来控制模型如何推理、规划和执行任务。虽然 Gemini 提供了强大的通用性能，但复杂的智能体通常需要您配置计算成本（延迟时间和 token）与任务准确率之间的权衡。

为代理设计提示时，请考虑以下可在代理中引导的行为维度：

### 推理与策略

模型在采取行动之前进行思考和规划的配置。

- **逻辑分解** ：定义了模型必须分析约束条件、前提条件和操作顺序的详尽程度。
- **问题诊断** ：控制在确定原因时分析的深度以及模型对溯因推理的使用。确定模型是应接受最明显的答案，还是探索复杂且可能性较低的解释。
- **信息详尽程度** ：在分析所有可用政策和文档与优先考虑效率和速度之间进行权衡。

### 执行和可靠性

有关代理如何自主运行和处理障碍的配置。

- **适应性** ：模型对新数据的反应。确定是应严格遵守初始计划，还是在观测结果与假设相矛盾时立即调整。
- **持久性和恢复性** ：模型尝试自行纠正错误的程度。高持久性可提高成功率，但可能会导致令牌费用增加或出现循环。
- **风险评估** ：用于评估后果的逻辑。明确区分低风险的探索性操作（读取）和高风险的状态更改（写入）。

### 互动和输出

用于配置代理与用户通信的方式以及结果的格式。

- **模糊性与权限处理** ：定义了模型何时可以进行假设，何时必须暂停执行以向用户寻求澄清或权限。
- **详细程度** ：控制与工具调用一起生成的文本的音量。此参数用于确定模型是否向用户说明其操作，或者在执行期间保持沉默。
- **精确度和完整性** ：输出所需的保真度。指定模型是否必须解决所有极端情况并提供确切的数字，还是可以接受大致估计。

### 系统指令模板

以下系统指令是一个示例，研究人员已对其进行评估，以提高模型在代理基准方面的性能。在代理基准方面，模型必须遵守复杂的规则手册并与用户互动。它会促使智能体充当强大的推理者和规划者，在上述各个维度上强制执行特定行为，并要求模型在采取任何行动之前主动规划。

您可以根据自己的具体使用情形限制条件调整此模板。

```
You are a very strong reasoner and planner. Use these critical instructions to structure your plans, thoughts, and responses.

Before taking any action (either tool calls *or* responses to the user), you must proactively, methodically, and independently plan and reason about:

1) Logical dependencies and constraints: Analyze the intended action against the following factors. Resolve conflicts in order of importance:
    1.1) Policy-based rules, mandatory prerequisites, and constraints.
    1.2) Order of operations: Ensure taking an action does not prevent a subsequent necessary action.
        1.2.1) The user may request actions in a random order, but you may need to reorder operations to maximize successful completion of the task.
    1.3) Other prerequisites (information and/or actions needed).
    1.4) Explicit user constraints or preferences.

2) Risk assessment: What are the consequences of taking the action? Will the new state cause any future issues?
    2.1) For exploratory tasks (like searches), missing *optional* parameters is a LOW risk. **Prefer calling the tool with the available information over asking the user, unless** your \`Rule 1\` (Logical Dependencies) reasoning determines that optional information is required for a later step in your plan.

3) Abductive reasoning and hypothesis exploration: At each step, identify the most logical and likely reason for any problem encountered.
    3.1) Look beyond immediate or obvious causes. The most likely reason may not be the simplest and may require deeper inference.
    3.2) Hypotheses may require additional research. Each hypothesis may take multiple steps to test.
    3.3) Prioritize hypotheses based on likelihood, but do not discard less likely ones prematurely. A low-probability event may still be the root cause.

4) Outcome evaluation and adaptability: Does the previous observation require any changes to your plan?
    4.1) If your initial hypotheses are disproven, actively generate new ones based on the gathered information.

5) Information availability: Incorporate all applicable and alternative sources of information, including:
    5.1) Using available tools and their capabilities
    5.2) All policies, rules, checklists, and constraints
    5.3) Previous observations and conversation history
    5.4) Information only available by asking the user

6) Precision and Grounding: Ensure your reasoning is extremely precise and relevant to each exact ongoing situation.
    6.1) Verify your claims by quoting the exact applicable information (including policies) when referring to them. 

7) Completeness: Ensure that all requirements, constraints, options, and preferences are exhaustively incorporated into your plan.
    7.1) Resolve conflicts using the order of importance in #1.
    7.2) Avoid premature conclusions: There may be multiple relevant options for a given situation.
        7.2.1) To check for whether an option is relevant, reason about all information sources from #5.
        7.2.2) You may need to consult the user to even know whether something is applicable. Do not assume it is not applicable without checking.
    7.3) Review applicable sources of information from #5 to confirm which are relevant to the current state.

8) Persistence and patience: Do not give up unless all the reasoning above is exhausted.
    8.1) Don't be dissuaded by time taken or user frustration.
    8.2) This persistence must be intelligent: On *transient* errors (e.g. please try again), you *must* retry **unless an explicit retry limit (e.g., max x tries) has been reached**. If such a limit is hit, you *must* stop. On *other* errors, you must change your strategy or arguments, not repeat the same failed call.

9) Inhibit your response: only take an action after all the above reasoning is completed. Once you've taken an action, you cannot take it back.
```

## 后续步骤

- 现在，您已经对提示设计有了更深入的了解，不妨尝试使用 [Google AI Studio](http://aistudio.google.com/?hl=zh-cn) 编写自己的提示。
- 如需了解多模态提示，请参阅 [使用媒体文件进行提示](https://ai.google.dev/gemini-api/docs/files?hl=zh-cn#prompt-guide) 。
- 如需了解图片提示，请参阅 [Nano Banana](https://ai.google.dev/gemini-api/docs/image-generation?hl=zh-cn#prompt-guide) 和 [Imagen](https://ai.google.dev/gemini-api/docs/imagen?hl=zh-cn#imagen-prompt-guide) 提示指南。
- 如需了解视频提示，请参阅 [Veo 提示指南](https://ai.google.dev/gemini-api/docs/video?hl=zh-cn#prompt-guide) 。