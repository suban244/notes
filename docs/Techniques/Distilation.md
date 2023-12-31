Generally 
- A large teacher model and a smaller student model.
- We try to match the output logits of teacher model by the student model.
![[Pasted image 20231226163657.png]]
## Issue with softmax
From the original paper
- Softmax pushes non target labels towards very small values 
- Softmax tends to hide the similarity between other classes (which are not the target)
	- Example: Say a **2** can be more similar to a **7**, than a **8**.
**Insight**: If we make the values of logits smaller before passing into softmax function, they retain some relativeness
### Temperature
Used to more smooth the output of softmax
$$\frac {\exp(5/T)} {\exp(5/T) + \exp(1/T)}$$
More generally. Here T is a hyper parameter
$$\frac {\exp(z_i/T)} {\sum_j \exp(z_j/T)}$$
*We choose a T such that it removes the impurities but preserves the elements*
![[Pasted image 20231226191614.png]]
### Losses
Use of Cross Entropy Loss / L2 loss between the probablities
## Intermediate match (Weights/Features)
- FC used to align dimensions
![[Pasted image 20231226164607.png]]
### Ways of distillation
![[Pasted image 20231226165420.png]]
#### Function Matching
Out of distribution data for teacher and the student