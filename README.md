# 驼铃 CamelBell-Chinese-LoRA

CamelBell (驼铃) is be a Chinese Language Tuning project based on LoRA. CamelBell is belongs to Project Luotuo([骆驼](https://github.com/LC1332/Chinese-alpaca-lora)), an open sourced Chinese-LLM project created by 冷子昂 @ 商汤科技 &amp; 陈启源 @ 华中师范大学 &amp; 李鲁鲁 @ 商汤科技  

CamelBell is NOT an official product of SenseTime

## News

[2023-3-24] We've just released Evaluation code, tuning Chinese LLM with very few data on GLM-6B via LoRA, try [here](https://colab.research.google.com/github/LC1332/CamelBell-Chinese-LoRA/blob/main/notebook/CamelBell_evaluation_code.ipynb) <a href="https://colab.research.google.com/github/LC1332/CamelBell-Chinese-LoRA/blob/main/notebook/CamelBell_evaluation_code.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>


## A Quick Demo

Check our evaluation code here <a href="https://colab.research.google.com/github/LC1332/CamelBell-Chinese-LoRA/blob/main/notebook/CamelBell_evaluation_code.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a> .

https://user-images.githubusercontent.com/5266090/227672185-3f4905ca-417b-4fe7-9dcf-30c5fef2e542.mov

## Training

We have tuned a Chinese model based on [ChatGLM-6B](https://github.com/THUDM/ChatGLM-6B) 

The training code was baed on [ChatGLM-Tuning](https://github.com/mymusise/ChatGLM-Tuning). However, the original code of ChatGLM-Tuning is still in building and not support Chinese Tuning. We modified part of training code. 

Our training code is in cleaning, if you are in hurry, check the ChatGLM-Tuning project and try to debug the part of Tokenizer and INT4/INT8 switcher stuff.

## Data

This is an inbuilding project, we plan to finish at least 3 demo LoRA models in this project

A. The model A will tuned on very few instruction (only around 80 questions, see in [developer_instruction.json](data/developer_instruction.json)), the model has been released now

B. The model B, we plan to do something interesting. 李鲁鲁 plan to write a script, selecting a character in a movie/ a book/ or history, query thousands of QA data from OpenAI api. and tuning GLM into a character chat bot.

C. The model C, find some specific domain QA data.

## TODO

inbuilding project

- [x] release evaluation code
- [x] release model A
- [ ] write data scipt for model B
- [ ] collecting data for model B
- [ ] release model B
- [ ] collecting data for model C
- [ ] release model C
- [ ] clean and release training code
- [ ] refactor GLM code into standard HuggingFace pipeline 

## Sponsorships(赞助)

Detailed Sponsorship and Balance see in [Sponsorship_and_balance.md](https://github.com/LC1332/Chinese-alpaca-lora/blob/main/data/Sponsorship_and_balance.md)

Top 3 Sponsorship until 3/24, this table in sub-repo may delay than the [major Luotuo](https://github.com/LC1332/Chinese-alpaca-lora)

| Time      | Sponsor     | Amount | Balance |
| --- | --- | --- | --- |
| 2023/3/24 | [yiplee](https://github.com/pandodao/botastic)      | 512    |  | |
| 2023/3/24 | Hijun       | 500    | | |
| 2023/3/24 | 倪**       | 500    | | |

[骆驼](https://github.com/LC1332/Chinese-alpaca-lora)原本是我们的一个作业项目，我们原本计划训练到1.0为止。但是社区的热情超过了我们的想象。如果您愿意赞助我们的项目，可以

扫描这个[二维码](https://s1.imagehub.cc/images/2023/03/23/fba44d198f0bb887089b4d8739363c0b.jpeg)

并且加这个[支付宝](https://s1.imagehub.cc/images/2023/03/23/b69e4e47759132dd3d4bbafa7bd602aa.jpeg)账号，留下您的姓名

项目的资金流向将被公开，所有的资金将被用于数据的标注，训练算力的购买或者后续周边产品的发放。数据和算力的捐献也会一同总结在sponsorship的表格中。备用链接 [二维码](https://github.com/LC1332/Chinese-alpaca-lora/blob/main/image/sponser_QR_code.jpeg) , [支付宝](https://github.com/LC1332/Chinese-alpaca-lora/blob/main/image/alipay_friend.jpeg)账号

This was originally an exercise project for us, and we originally planned to train until version 1.0. However, the enthusiasm of the community exceeded our expectations. If you are willing to sponsor our project, you can scan this [QR code](https://github.com/LC1332/Chinese-alpaca-lora/blob/main/image/sponser_QR_code.jpeg)  and add [this Alipay account](https://github.com/LC1332/Chinese-alpaca-lora/blob/main/image/alipay_friend.jpeg), leaving your name.

All funds will be used for data annotation, purchase of training computing power, or distribution of subsequent peripheral products.

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

