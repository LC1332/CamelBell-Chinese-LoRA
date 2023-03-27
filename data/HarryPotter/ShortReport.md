# ChatHarryPotter: A Brief Report for First Experiment

我们希望使用LoRA训练的方式，基于GLM-6B的语言模型，finetune得到一个能够扮演哈利波特的ChatBot。我们做了初步实验，模型能够组织输出很多与魔法世界相关的句子，但是真实性与哈利波特的小说往往不吻合。我们将初步的模型命名为ChatHarryPotter-0.1。在更符合哈利波特小说的模型出现前，我们并没有准备直接release这个模型。这篇文章介绍了0.1模型的训练过程和基本的表现。我们正在积极寻找**一个高质量的Python程序员，同时他需要是Harry Potter故事的狂热粉丝**，来加入到我们的项目中。

With the LoRA, based on the GLM-6B language model, we aim to fine-tune a ChatBot which can cos-play Harry Potter. In our preliminary experiments, the model generates many sentences related to the magical world, but they often failed to match the authenticity of the Harry Potter novels. We have named the preliminary model ChatHarryPotter-0.1. We are not ready to release this model until a more accurate model based on the Harry Potter novels is developed. This article introduces the training process and basic performance of the 0.1 model. We are actively looking for **a solid Python programmer who is also a Harry Potter enthusiast** to join our project.

## Data


### Good Example

'''
Instruction: 问题:霍格沃滋是什么?
Answer: 霍格沃茨是一所魔法学校,位于英格兰的霍格沃茨镇。霍格沃茨是魔法世界中最著名的魔法学校之一,也是许多魔法学生的梦想之地。霍格沃茨成立于1939年,由哈利波特的父亲詹姆·波特和母亲莉莉·波特创立。霍格沃茨是一所魔法学校,提供魔法课程和魔法教学。
'''


### Bad Example


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

