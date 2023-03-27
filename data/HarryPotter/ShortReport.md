# ChatHarryPotter: A Brief Report for First Experiment

我们希望使用LoRA训练的方式，基于GLM-6B的语言模型，finetune得到一个能够扮演哈利波特的ChatBot。我们做了初步实验，模型能够组织输出很多与魔法世界相关的句子，但是真实性与哈利波特的小说往往不吻合。我们将初步的模型命名为ChatHarryPotter-0.1。在更符合哈利波特小说的模型出现前，我们并没有准备直接release这个模型。这篇文章介绍了0.1模型的训练过程和基本的表现。我们正在积极寻找**一个高质量的Python程序员，同时他需要是Harry Potter故事的狂热粉丝**，来加入到我们的项目中。

With the LoRA, based on the GLM-6B language model, we aim to fine-tune a ChatBot which can cos-play Harry Potter. In our preliminary experiments, the model generates many sentences related to the magical world, but they often failed to match the authenticity of the Harry Potter novels. We have named the preliminary model ChatHarryPotter-0.1. We are not ready to release this model until a more accurate model based on the Harry Potter novels is developed. This article introduces the training process and basic performance of the 0.1 model. We are actively looking for **a solid Python programmer who is also a Harry Potter enthusiast** to join our project.

## First Impression

### Good Example

```
Instruction: 斯内普和伏地魔之间是什么关系?
Answer: 斯内普和伏地魔之间是非常复杂的关系。伏地魔是斯内普的雇主,他利用斯内普来执行他的计划。斯内普一开始是斯莱特林的学生,但他后来加入了伏地魔的阵营,成为了他的追随者。斯内普和伏地魔之间的关系非常紧张,他们互相对抗,但也有一些共同的利益。
```

```
Instruction: 你怎么认识的赫敏?
Answer: 我和赫敏是在霍格沃茨魔法学校的第一年认识的。当时,赫敏是一个年轻的女巫师,她和我同班,我们一起学习魔法和应对各种挑战。赫敏是一个非常聪明、勇敢和善良的女孩,她在整个魔法世界中都有很高的声望。
```

### Bad Example

```
Instruction: 谁有隐身斗篷?
Answer: 赫敏·格兰杰有隐身斗篷。在《哈利波特与密室》中,赫敏使用隐身斗篷来躲避伏地魔的追踪。
```

```
Instruction: 老魔杖的最后的主人是谁?
Answer: 老魔杖的最后的主人是哈利波特的父亲詹姆·波特。在《哈利波特与密室》中,詹姆·波特被伏地魔的追随者贝拉特里克斯·莱斯特兰杀害。
```

从初步的实验可以看到，1. 模型可以输出基础的语句，这是因为GLM本身模型就已经拥有了基础的语言输出能力。 2. 模型正确学会了哈利波特的世界的语法关系，模型显然知道有些词语是人，有些词语是物体，并且有些非常规的短语，比如咒语，并且将这些句子放到句子中正确的位置。3.模型可以记忆和推断一部分哈利波特的内容，并且我们检索了训练语料，模型回答的内容与训练语料并不是完全一致的。

在更多的情况(70%-80%)下，模型会输出“错误”的回答。1. 在大多数的错误案例中，模型容易说出与事实（哈利波特小说和电影中的事实）不符的回答。







### More Good Example

```
Instruction: 霍格沃滋是什么?
Answer: 霍格沃茨是一所魔法学校,位于英格兰的霍格沃茨镇。霍格沃茨是魔法世界中最著名的魔法学校之一,也是许多魔法学生的梦想之地。霍格沃茨成立于1939年,由哈利波特的父亲詹姆·波特和母亲莉莉·波特创立。霍格沃茨是一所魔法学校,提供魔法课程和魔法教学。
```


### More Bad Example

```
Instruction: 死亡圣器有哪些?
Answer: 死亡圣器是指在《哈利波特》系列小说中被提及的死亡圣器。它们分别是:

1. 死亡圣器之剑:霍格沃茨的校长邓布利多曾经持有一把死亡圣器之剑,这把剑可以杀死任何敌人。

2. 死亡圣器之杖:霍格沃茨的校长邓布利多曾经持有一把死亡圣器之杖,这把杖可以杀死任何敌人。

3. 死亡圣器之戒:霍格沃茨的校长邓布利多曾经持有一只死亡圣器之戒,这个戒指可以杀死任何敌人。

死亡圣器是哈利波特
```

## Data


我们简单尝试模仿Alpaca的方法，使用42个[seeds问题](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/seed_tasks.jsonl)，生成了1500个左右的中文问题，并且调用OpenAI的3.5-turbo接口，让OpenAI扮演Harry Potter进行回答。(一个短的版本 [这里](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/sample_output.json), 完整1500条的版本[这里](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/output.json))


Similiar to the Aplpaca project, we first seed [42 question](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/seed_tasks.jsonl), and to generate around 1500 Chinese questions. We then utilized OpenAI's 3.5-turbo API to cammend it play the role of Harry Potter and provide answers. (check a short sample version [here](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/sample_output.json), and the full 1500 [here](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/output.json))





## Citation

Please cite the repo if you use the data or code in this repo.

```
@misc{alpaca,
  author={Ziang Leng, Qiyuan Chen and Cheng Li},
  title = {Luotuo: An Instruction-following Chinese Language, LoRA tuning on LLaMA model},
  year = {2023},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/LC1332/Chinese-alpaca-lora}},
}
```

