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

The training code was baed on [ChatGLM-Tuning](https://github.com/mymusise/ChatGLM-Tuning). However, the original code of ChatGLM-TUning is still in building and not support Chinese Tuning. We modified part of training code. 

Our training code is in cleaning, if you are in hurry, check the ChatGLM-Tuning project and try to debug the part of Tokenizer and INT4/INT8 switcher stuff.

## Data

This is an inbuilding project, we plan to finish at least 3 demo LoRA models in this project

A. The model A will tuned on very few instruction (only around 80 questions, see in [developer_instruction.json](data/developer_instruction.json)), the model has been released now

B. The model B, we plan to do something interesting. 李鲁鲁 plan to write a script, selecting a character in a movie/ a book/ or history, query thousands of QA data from OpenAI api. and tuning GLM into a character chat bot.

C. The model C, find some specific domain QA data.

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

