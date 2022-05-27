## Improving CTC-based ASR Models with Gated Interlayer Collaboration

作者：Yuting Yang, Yuke Li, Binbin Du            
机构：网易         
关键词：CTC、流式、文本融合           
### 动机
ctc的独立性假设不合理，无法在模型前向中利用到文本信息

### 方法
encoder使用conformer       
提出一种融合方法gated interlayer collaboration （GIC）   
首先将隐状态过一个线性层映射到字典维度得到后验，之后过embedding得到textual feature     

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653620245806/9-pCZOsHA.png align="left")

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653620256457/qabF0GuNs.png align="left")

通过门控的方式融合两个模态

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653620298741/K8ecK9ker.png align="left")
最终loss是原本的ctcloss加上所有的中间CTC的平均值

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653620353727/4jlpuJez_.png align="left")
### 实验
#### 实验设置


- 实验数据
aishell-1 数据堂
#### 实验结果

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1653627039503/eTfIiAjja.png align="left")



### 总结
其实跟
[Relaxing the Conditional Independence Assumption of CTC-based ASR
by Conditioning on Intermediate Predictions](https://arxiv.org/pdf/2104.02724.pdf)
相比就是加了一个embedding和加权相加
