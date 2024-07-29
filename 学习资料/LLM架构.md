# Transformer
> [Attention Is All You Need](https://arxiv.org/pdf/1706.03762)
![[Pasted image 20240729193928.png]]
# LLM简介
## Llama3.1模型架构
![[Pasted image 20240729194856.png]]
## 简介
简单来说，LLM是一个生成式模型，根据目前的序列，预测下一个词，再把这个词加入到序列中，再预测下一个词，循环往复直到生成结束标记。
例如：
```
input:你是谁？
"你是谁"(seq)->tokenizer(分词器)->["你"对应的token_id,"是"对应的token_id,"谁"对应的token_id]
token_id->embedding层->向量化的token
向量化的序列->
```