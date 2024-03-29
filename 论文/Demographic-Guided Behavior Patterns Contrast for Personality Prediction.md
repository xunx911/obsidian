# 简介

实验结果表明,通过对比不同学习者的粗略行为模式,人口统计学指导的有监督对比学习能够缓解类别分布不平衡带来的负面影响.此外,与统计行为信息相比,序列行为信息可以帮助我们的DGBPC模型更细粒度地分析学习者的行为模式,并准确地对学习者的性格进行分类.
![[Pasted image 20240206163614 1.png]]
Demographic-Guided Behavior Patterns Contrast (DGBPC) model

1. 对比学习者选择组选择对比组
2. 提取精细行为模式
3. 粗行为模式提取模块从细行为模式中进行提取
4. 粗模式对比模块将学习者与其对比组的粗行为模式进行对比
5. 人格分类模块进行分类

对于五种人格特质之一的M类人格特质分类任务,目标学习者$u∈U$,带有学习行为序列$S_u \{ s_1,s_2,...,s_T\}$,每个学习活动$s_t$ 具有n维特征,$d_u$是$u$的人口统计学特征,具有z维,$F_u,R_u$是对应的细模式和粗模式.

# 1

$从U中各选了k个和u相同人格的以及不同人格的,组成了K个对比组$.具体来说，在为学习者$u$选择第$i个对比组\{u^s_i，u^d_i\}时，根据u和其他学习者∈U的人口统计特$征集计算余弦相似度。然后进行排序。然后，$选择与学习者u具有相同性格类别的第i个$学习者和与学习者$u$具有不同性格类别的第$i个学习者。选取的两个学习者将是第i个学习者u的对比组.$

# 2

![[Pasted image 20240206170656 1.png]]
![[Pasted image 20240206171603 1.png]]一阶和二阶特征交互
![[Pasted image 20240206205416.png]]加上人口统计学特征
![[Pasted image 20240206205444.png]]

# 3

![[Pasted image 20240206205741.png]]

# 4

![[Pasted image 20240206212715.png]]
$对u来说,拉近与u^s的距离,拉远与u^d的距离$

# 5

We use the fine behavior patterns of the learners to classify their personalities.
![[Pasted image 20240207115059.png]]
人格分类时使用的是精细行为模式$F_u$放入一个线性层和一个softmax层得到概率分布,参见模型图,箭头是从精细行为模式出来的.最后交叉熵损失疑似真实值和预测值反了

# 数据集

![[Pasted image 20240207120844.png]]
![[Pasted image 20240207120853.png]]
主流数据集没有行为数据,要么是private的小数据集
极端人格分布不均衡问题
![[Pasted image 20240207121927.png]]
6个行为特征是数值特征,人口统计学特征为分类特征oh编码



...各种消融实验,sota