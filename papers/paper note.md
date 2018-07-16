### Abstract

**本文基于四个假设**

a) memories can be formed from word sequences by using convolutional networks; 

b) distance measurements can be taken at a neuronal level; 

c) a recursive soft-max function can be used for attention; 

d) extensive weight sharing can help profoundly. 



### Introduction 

**架构的基本假设**

1. 文本数据由embedding layer[Mikolov et al., 2013] 转换为实值向量
2. 这些向量序列由one-dimensional convolutional layer[LeCun et al., 1998]处理
3. 没看懂 ...
4. 文字向量序列由maxpooling layer处理，目的是为了subsample信息到activations激活函数，这些activations大体的包含了原文本信息，在这个阶段，压缩了句子和问题数据，然后执行所谓的matching操作，目的是识别出每个不同的句子和问题（被压缩过的）。这个matching操作帮助神经网络识别source data中的哪些bit最像对问题的回答有帮助的。(This results in a separate match vector for each sentence-question pair. Following that, we perform a non-linear transformation to each matched sentence-question pair.  )
5. 启动一个定时的softmax attention程序循环遍历sentence-question pair，找到一个包含最相关的信息的向量。然后我们feed这个向量给another recurrence，作为complementary question。大概3次这样的recurrent loops，我们就将最后的输出交给softmax layer 去提供最后的answer

### background

1. .... 
2. 所需的预处理量是一个有趣的差异点，有些是在句子级别提取特征，本文是在Word级别。



### Neural Architecture

- input encoding

  embedding layer 逐个处理Word，首先每个each word is encoded as a vector of length n neurons,