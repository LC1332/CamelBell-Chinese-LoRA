# 驼铃 CamelBell-Chinese-LoRA

CamelBell (驼铃) is be a Chinese Language Tuning project based on LoRA. CamelBell is belongs to Project Luotuo([骆驼](https://github.com/LC1332/Luotuo-Chinese-LLM)), an open sourced Chinese-LLM project created by 冷子昂 @ 商汤科技 &amp; 陈启源 @ 华中师范大学 &amp; 李鲁鲁 @ 商汤科技  

CamelBell is NOT an official product of SenseTime

## News

[2023-3-30] We released Chinese Summarization Model, CamelBell-C (驼铃-C), try in this <a href="https://colab.research.google.com/github/LC1332/Luotuo-Chinese-LLM/blob/main/notebook/TuoLingC_evaluation_code.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>.

```
Instruction: 请帮我总结以下内容:
Input: 
北京时间2月13日凌晨,2023年ATP250达拉斯站男单决赛。中国球员吴易昺先输一盘后挽救4个赛点并兑现第5个冠军点,最终以6(4)-7/7-6(3)/7-6(12)逆转惊险击败赛会5号种子、美国大炮伊斯内尔,就此改写历史,成为公开赛年代首位夺得ATP巡回赛男单冠军的中国大陆球员,并创造中国大陆球员的男单最高排名!

第一盘比赛,吴易昺在第12局错过了一个盘点,并最终抢七惜败;第二盘则挽救一个赛点后抢七局3-0领先开局,且以7-6(3)扳回一盘;第三盘决胜盘,在关键的第9局15-40落后情况下凭借连续的高质量发球逆转保发,之后比赛再次进入抢七,抢七局依然胶着,吴易昺又挽救了3个赛点,并兑现了自己的第5个冠军点,就此锁定冠军!历史性一刻到来时,吴易昺瞬间躺倒在地。全场比赛,伊斯内尔轰出了44记Ace球,但最终在主场依然输给了吴易昺。

凭借具有突破意义的这一冠,吴易昺在本周入账250个积分和112125美元的冠军奖金,在周一最新一期的男单排名榜单上,创中国大陆男网历史新高排名—第58位。根据比赛计划,吴易昺原本要出战本周进行的ATP250德拉海滩站,不过在达拉斯夺冠后,吴易昺因身体疲劳退出本站赛事,他的签位由幸运落败者约翰森替代。

Answer: 男子网坛历史性一刻!中国小将吴易昺逆转击败赛会5号种子,成公开赛年代首个冠军。
```


[2023-3-27] We plan to train a [ChatHarryPotter](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/ShortReport.md), we've just finished the prelimiary experiment and have ver. 0.1 model, but it did not meet our expectation, see this [report](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/ShortReport.md), and we are pursuing *a Harry Potter enthusiast Pythoner to join*.

[2023-3-24] We've just released Evaluation code, tuning Chinese LLM with very few data on GLM-6B via LoRA, try [here](https://colab.research.google.com/github/LC1332/CamelBell-Chinese-LoRA/blob/main/notebook/CamelBell_evaluation_code.ipynb) <a href="https://colab.research.google.com/github/LC1332/CamelBell-Chinese-LoRA/blob/main/notebook/CamelBell_evaluation_code.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>


## CamelBell-A

驼铃-A是一个小型的实验，仅仅使用80条语料，1小时的训练时间（A100），将开发者的信息Encode到LoRA之中。初步验证了在中文基模型上使用超小语料finetune的可行性。  <a href="https://colab.research.google.com/github/LC1332/CamelBell-Chinese-LoRA/blob/main/notebook/CamelBell_evaluation_code.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a> .

https://user-images.githubusercontent.com/5266090/227672185-3f4905ca-417b-4fe7-9dcf-30c5fef2e542.mov

## CamelBell-B

We are building CamelBell-B, ChatHarryPotter, we now have a 0.1 version, check the [report](https://github.com/LC1332/CamelBell-Chinese-LoRA/blob/main/data/HarryPotter/ShortReport.md) here.

## CamelBell-C

驼铃-C是一个中文摘要模型，我们在字节发布的CNewSum数据集上，抽样了210k条语句进行训练。 <a href="https://colab.research.google.com/github/LC1332/Luotuo-Chinese-LLM/blob/main/notebook/TuoLingC_evaluation_code.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>.

```
Instruction: 请帮我总结以下内容:
Input: 从招聘网站的搜索结果来看,目前游戏厂商对于AIGC人才的招聘,主要分为两个方向,一是更加针对性的AI美术方向,二则是相对面向AIGC生产流程构建底层的算法工程师。

在AI画图技术证明了自己的产出能力之后,就早已有游戏公司迅速开始了布局。似乎从2022年底开始,就时常能够听到某家游戏大厂内部已经将AI美术产出流程跑通的消息,光是这个月就有恺英网络、完美世界等几家大厂宣布了入局AIGC技术应用的消息。

在快速进行内部摸索的同时,有厂商也寻求外部人才协助,想要实现AI绘图创作通路的快速落地。倘若在招聘网站上搜索AI绘画,将范围限定在“游戏”方面,就已经能看到不少相关职业。其中包括巨人网络、成都IGG、厦门梦加游戏等游戏厂商都放出了相应的岗位需求,要求应聘者熟悉Midjoumey、Stable Diffusion这类AI美术工具,开出的价格也在10K到35K之间不等。

广州的四三九九的AI绘图岗位除了对应聘者的AI艺术工具使用熟练度有要求之外,在岗位职责里,还加入了“帮助美术部门了解和使用AI及相关工具,协助研队提高对AI的使用度和效率”的需求,想要通过招聘专业的AIGC人才来培养内部的美术团队AIGC创作能力。

另外寻求外部人才培养美术团队AIGC能力的还有腾讯,在某个远未来科幻欧卡SLG项目的AI原画招聘需求中,除了研究和生产AI美术素材之外,还需要应聘者充实公司AI词库,并定期对美术团队进行培训,提升团队AI美术工具的熟练
Answer: 游戏公司招聘AIGC人才,要求熟悉AI美术工具,开出价格从10K到35K不等。
```

```
Instruction: 请帮我总结以下内容:

Input: 美国硅谷银行 (Silicon Valley Bank, SVB ;矽谷银行)和“标志银行”(Signature Bank,又译“签名银行”)在几天内相继倒闭后,美国当局采取了紧急措施来支撑银行系统。这是美国自2008年金融海啸以来最大的银行倒闭事件,恐引起金融市场骨牌效应。硅谷银行因资不抵债在48小时内倒闭后,3月10日由美国联邦存款保险公司(FDIC)接管。美国财政部、联储局及联邦存款保险公司12日晚间发表联合声明指,正采取果断行动,以增强公众对银行体系的信心,并向硅谷银行存户保证,可以在13日周一取回所有存款。

3月12日,美国财政部以存在系统性风险为由关闭总部设在纽约州的“标志银行”。该银行是加密货币公司的主要融资来源之一。美国总统拜登发表讲话,承诺将“竭尽所能”保护银行系统。但投资者担心其他银行可能仍会受到影响,引发全球股价大幅下跌。事件震荡全球金融市场,加拿大、英国等多个市场都受牵连。法兰克福、巴黎和米兰的股市大幅下跌。周一(3月13日)早些时候,西班牙桑坦德银行(Santander)和德国商业银行(Commerzbank)的股价一度下跌超过10%。极地资本(Polar Capital)基金经理乔治·戈德伯(George Godber)表示,市场下跌是因为“担心那里可能还有其他事情发生”。他说:“迫在眉睫的危机可能已经避免,但它提醒人们注意这样一个事实,即有一群公司的商业模式将在高利率环境中苦苦挣扎。”但他表示,事件对英国经济和英国市场的直接影响有限。BBC中文梳理这次危机的来龙去脉,以及对全球的影响。

Answer: 硅谷银行和“标志银行”倒闭,美国当局采取紧急措施支撑银行系统。
```

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

Detailed Sponsorship and Balance see in [Sponsorship_and_balance.md](https://github.com/LC1332/Luotuo-Chinese-LLM/blob/main/data/Sponsorship_and_balance.md)

Top 3 Sponsors(爸爸) until 3/24, this table in sub-repo may delay than the [major Luotuo](https://github.com/LC1332/Luotuo-Chinese-LLM)

| Time     | Sponsor     | Amount |
| --- | --- | --- |
| 2023/3/25 | [肖**]( https://github.com/mobe1978)  | 520 |
| 2023/3/24 | *潇      | 518    |
| 2023/3/24 | [yiplee](https://github.com/pandodao/botastic)  | 512 |

[骆驼](https://github.com/LC1332/Luotuo-Chinese-LLM)原本是我们的一个作业项目，我们原本计划训练到1.0为止。但是社区的热情超过了我们的想象。如果您愿意赞助我们的项目，可以

扫描这个[二维码](https://s1.imagehub.cc/images/2023/03/23/fba44d198f0bb887089b4d8739363c0b.jpeg)

并且加这个[支付宝](https://s1.imagehub.cc/images/2023/03/23/b69e4e47759132dd3d4bbafa7bd602aa.jpeg)账号，留下您的姓名

项目的资金流向将被公开，所有的资金将被用于数据的标注，训练算力的购买或者后续周边产品的发放。数据和算力的捐献也会一同总结在sponsorship的表格中。备用链接 [二维码](https://github.com/LC1332/Luotuo-Chinese-LLM/blob/main/image/sponser_QR_code.jpeg) , [支付宝](https://github.com/LC1332/Luotuo-Chinese-LLM/blob/main/image/alipay_friend.jpeg)账号

This was originally an exercise project for us, and we originally planned to train until version 1.0. However, the enthusiasm of the community exceeded our expectations. If you are willing to sponsor our project, you can scan this [QR code](https://github.com/LC1332/Luotuo-Chinese-LLM/blob/main/image/sponser_QR_code.jpeg)  and add [this Alipay account](https://github.com/LC1332/Chinese-alpaca-lora/blob/main/image/alipay_friend.jpeg), leaving your name.

All funds will be used for data annotation, purchase of training computing power, or distribution of subsequent peripheral products.

## Citation

Please cite the repo if you use the data or code in this repo.

```
@misc{alpaca,
  author={Ziang Leng, Qiyuan Chen and Cheng Li},
  title = {Luotuo: An Instruction-following Chinese Language model, LoRA tuning on LLaMA},
  year = {2023},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/LC1332/Luotuo-Chinese-LLM}},
}
```

