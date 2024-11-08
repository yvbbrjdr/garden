---
title: 语言模型参数量、计算量估计
---
本文汇总语言模型各组件参数量以及计算量。
## Tokenizer

将字符串分割成 token array，并查表找到各 token 的 embedding。

参数量为 token 总量 x embedding 维度。

| 模型            | Token 总量 | Embedding 维度 | 参数总量       |
| ------------- | -------- | ------------ | ---------- |
| Llama 3.1 70b | 128000   | 8192         | 1048576000 |

_未完_