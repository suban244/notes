---
tags:
  - Vision-Transformers
  - Knowledge-Distillation
  - facebook
---
Data efficient [image transformers](ViT.md) & distillation through attention
- [Heavy image augmentation](Deit#Augmentation)
- [Distillation token](DeIT#Distillation-Token)
- [Regularization](DeIT#Regularization)
## Results
- competitive result at imagenet with no external data and less compute
	- When pretrained on imagenet, good result on downstream tasks.
## Regularization
- [[Erasing]]
- [[Stochastic Depth]]
- [[Repeated Augmentation]]
The first two being crucial for convergence
Not applied but cool
- [[Dropout]]
- [[Exponentially Moving average]]
## Augmentation
There is a need for heavy augmentation
- Rand-Augment
- Mixup
- CutMix
Not applied but interesting
- Auto augmentation
## Distillation-Token
A different technique compared to the usual [[Distilation]]
- Use of a teacher-student architecture 
	- Convnet is a better teacher than Transformers
	- Prob because of inductive bias	
![[Pasted image 20231227113323.png]]	
- Use of a separate distillation token, 
	- starts out different from the class token, (does different things)
	- at the end has high similarity with class token
	- It is different from class token
- Less training required for good results.
### How Trained ?
- for soft, use of KL divergence between teacher and student as loss
- for hard, same as classification loss (we can use label smoothing for soft labels)
### At inference
- Use of both class and distillation token 
