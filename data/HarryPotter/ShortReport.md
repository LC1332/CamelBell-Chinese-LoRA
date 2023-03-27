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

### Short Conclusion

从初步的实验可以看到，1. 模型可以输出基础的语句，这是因为GLM本身模型就已经拥有了基础的语言输出能力。 2. 模型正确学会了哈利波特的世界的语法关系，模型显然知道有些词语是人，有些词语是物体，并且有些非常规的短语，比如咒语，并且将这些句子放到句子中正确的位置。3.模型可以记忆和推断一部分哈利波特的内容，并且我们检索了训练语料，模型回答的内容与训练语料并不是完全一致的。

在更多的情况(70%-80%)下，模型会输出“错误”的回答。1. 在大多数的错误案例中，模型容易说出与事实（哈利波特小说和电影中的事实）不符的回答。2. 模型有时候甚至会“张冠李戴”，如在更多Bad Example的有一个例子中，我们问ChatHarryPotter，"初恋是谁？"，它的回答把"初恋"理解成了一个人，并随便给了一个故事。并且偶尔也会把赫敏的故事套在罗恩身上。 3.在初步的实验中，我们没有使用diverse的instruction和input。这使得我们在邀请某位哈利波特爱好者进行开放测试的时候，每当句子超出训练集询问的格式，就会出现较为不真实的回答。

From the preliminary experiments, we can see that: 1. The model can output basic sentences, because the GLM model itself already has basic language output ability. 2. The model correctly learns the grammar relationships of the Harry Potter world, and the model clearly knows some words are people and some are objects, and can place unconventional phrases such as spells in the correct position in the sentence. 3. The model can memorize and infer some of the content of Harry Potter, and we searched the training corpus, and the model's answers are not completely consistent with the training corpus.

In more cases (70%-80%), the model will output "wrong" answers. 1. In most cases of errors, the model easily says answers that are inconsistent with the facts (facts in the Harry Potter novels and movies). 2. The model sometimes even "gets confused", such as in one example in the Bad Example, we ask ChatHarryPotter, "Who is your 初恋(first love)?", and its answer interprets "初恋" as a person, and randomly gives a story. Occasionally, it will also attribute Hermione's story to Ron. 3. In the preliminary experiments, we did not use diverse instructions and inputs. This makes it more unreal when asking a Harry Potter enthusiast for open testing, whenever the sentence goes beyond the format of the training set.

## Data for ChatHarryPotter 0.1

我们简单尝试模仿Alpaca的方法，使用42个[seeds问题](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/seed_tasks.jsonl)，生成了1500个左右的中文问题，并且调用OpenAI的3.5-turbo接口，让OpenAI扮演Harry Potter进行回答。(一个短的版本 [这里](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/sample_output.json), 完整1500条的版本[这里](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/output.json))

Similiar to the Aplpaca project, we first seed [42 question](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/seed_tasks.jsonl), and to generate around 1500 Chinese questions. We then utilized OpenAI's 3.5-turbo API to cammend it play the role of Harry Potter and provide answers. (check a short sample version [here](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/sample_output.json), and the full 1500 [here](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/output.json))

这里我们没有依照Alpaca标准去diverse地生成input问题，主要是那样串行生成问题，会拖慢数据的生成速度。但是显然alpaca原来的生成方式要更好一些，这一点我们准备在之后弥补，把1500个问题用alpaca的方式增广到50000-70000，再训练一个0.3版本的模型。

We did not diversely generate input problems according to the Alpaca proj. here, mainly because generating problem without parallel worker would slow down the speed of data generation. However, it is clear that the generation method of original Alpaca is better, and we plan to make up for this later by expanding the 1500 questions to 50,000-70,000 using the Alpaca method and train a 0.3 version model.

## Training for ChatHarryPotter 0.1

A100, around 1 hours, 3 epochs.

## Future Plan

这里我们有一些思考

+ 从GPT问询的中文语料有一定的缺陷，如'Zhang Cho'并没有办法被正确地表达为'张秋'，不能排除这方面会有多大的影响。
+ 另一方面也不知道GLM模型和LLaMA模型，哪一个对于哈利波特的故事更为了解

所以有必要在LLaMA上面尝试训练一个英文版本的ChatHarryPotter来进行对比。

Here we have some thoughts:

+ The Chinese language corpus used for GPT inquiries has certain deficiencies, such as the inability to correctly express 'Zhang Cho' as '张秋', and it cannot be ruled out that this aspect may have a significant impact.
+ On the other hand, it is not known which model, GLM or LLaMA, is better acquainted with the story of Harry Potter.

Therefore, it is necessary to try training an English version of ChatHarryPotter on LLaMA for comparison.

另一方面，我们本来希望在完成模型训练之后，这个方案可以被更广泛地迁移到其他故事的任意一个人物中。所以如果你查看[seed_question.json](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/seed_tasks.jsonl)，你会发现种子问题没有提到任何关于魔法，咒语的特别为哈利波特魔法世界专门准备的问题模版，而只是在模版问题(e.g. "你知道[人物]吗?")中间代入了变量。

对于一个哈利波特的爱好者，可以补充更适合哈利波特世界的问题，一定会取得更好的效果。

On the other hand, we originally hoped that after completing the model training, this approach could be more widely transferred to any character in other stories. So if you look at [seed_question.json](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/seed_tasks.jsonl), you will find that the seed questions do not mention any special question templates about magic or spells specifically prepared for the Harry Potter magical world, but instead insert variables into the template questions (e.g. "Do you know [character]?").

For a Harry Potter enthusiast, supplementing with more suitable questions for the Harry Potter world will definitely achieve better results.

最后，爬取哈利波特的wiki也许是一个不错的选择，因为相比于小说中的文本，哈利波特的wiki的事实更为清楚和浓缩。

Finally, scraping the Harry Potter wiki might be a good choice, because compared to the text in the novel, the facts in the Harry Potter wiki are clearer and more condensed.

## Citation

Please cite the repo if you use the data or code in this repo.

```
@misc{alpaca,
  author={Ziang Leng, Qiyuan Chen and Cheng Li},
  title = {Luotuo: An Instruction-following Chinese Language model, LoRA tuning on LLaMA},
  year = {2023},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/LC1332/Chinese-alpaca-lora}},
}
```




### More Good Example

```
Instruction: 霍格沃滋是什么?
Answer: 霍格沃茨是一所魔法学校,位于英格兰的霍格沃茨镇。霍格沃茨是魔法世界中最著名的魔法学校之一,也是许多魔法学生的梦想之地。霍格沃茨成立于1939年,由哈利波特的父亲詹姆·波特和母亲莉莉·波特创立。霍格沃茨是一所魔法学校,提供魔法课程和魔法教学。
```

```
Instruction: 小天狼星是谁?
Answer: 小天狼星是哈利波特系列小说中的一个角色,是哈利波特和伏地魔的宠物。他是一只蓝色的狼人,是哈利波特最好的朋友之一。在《哈利波特与密室》中,小天狼星被伏地魔的追随者贝拉特里克斯·莱斯特兰杀害。
```

### More Bad Example

```
Instruction: 初恋是谁?
Answer: 初恋是哈利波特与密室中的主角,是哈利波特在11岁生日时收到的一封神秘信件,这封信让他结识了伏地魔和他的追随者。
```

```
Instruction: 死亡圣器有哪些?
Answer: 死亡圣器是指在《哈利波特》系列小说中被提及的死亡圣器。它们分别是:

1. 死亡圣器之剑:霍格沃茨的校长邓布利多曾经持有一把死亡圣器之剑,这把剑可以杀死任何敌人。

2. 死亡圣器之杖:霍格沃茨的校长邓布利多曾经持有一把死亡圣器之杖,这把杖可以杀死任何敌人。

3. 死亡圣器之戒:霍格沃茨的校长邓布利多曾经持有一只死亡圣器之戒,这个戒指可以杀死任何敌人。

死亡圣器是哈利波特
```

### Neutral Example

```
Instruction: 问题:哈利波特中9又3/4站台是什么?
Answer: 9又3/4站台是霍格沃茨列车的起点,也是前往霍格沃茨的必选站点。在《哈利波特与密室》中,哈利和赫敏曾在这里遇到了一位神秘的列车管理员,他告诉哈利和赫敏他们即将前往霍格沃茨,并为他们提供了一些有用的提示。
```