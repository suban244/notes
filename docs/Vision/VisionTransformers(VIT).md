# Overview
- Originally introduced at https://arxiv.org/abs/2010.11929
- Only Encoder used, proposes a pure transformer model for sequence of image patches.
	- Pass through a linear embedding layer
	- Tokens for transformer
- Pre-trained on image data
	- ImageNet, ... for classifcation task and then the head removed
	- require less computation
- Why Transformers?
	- Because *Transformers*
	- Also because they lack [[VisionTransformers(VIT)#Inductive Bias]], present in CNNs
	- And if we train on large enough dataset, we do not need any [[VisionTransformers(VIT)#Inductive Bias]]
![[Pasted image 20231218151913.png]]
## Related works
- [[BERT]] trained using self-supervised pre-training task, [[GPT]] with language modeling
- For Images
	- Pixel-wise is too expensive
	- Self attention to only local areas: can completely replace transformers.
	- Scalable approximation to global self attention *a paper*
	- 2x2 patches and self attention (works for small images)
## Inductive Bias
*Theoretically* a Fully connected neural network can approximate any function and thus any mapping.
We design certain network structures, using our understanding of a domain, so that a network can more easily learn about that particular domain
This introduces a bias, that helps the network do well.
- CNN: 
	- Locality
	- Translation Equivalent 
	- 2 Dimensional structure
- RNN:
	- The Sequence nature of the data
These are imposed from human understanding of the domain(images & language).
***We call them biases as they in a way restrict model's ability to learn a more general function. ?***
- Good for less amount of data
#### No need for inductive biases
- Inductive Bias helps when data is less. 
- But then data is plenty(303M or more idk), they can hinder 
# Details
## Steps
### Embedding
- Data -> Vectors
- In NLP, the data is generally a token
- In VIT: 
	- transform image into 16 x 16 patches
	- Rearrange('b c (h p1) (w p2) -> b (h w) (p1 p2 c)')
	- Fully connected neurons
$$\Large x \in R^{H \times W \times C} \rightarrow x_p \in R^{N \times (P^2C)} \Rightarrow z_0 \in R^{(1+N) \times D}$$
$\rightarrow$: Reshaping
$\Rightarrow$: Trainable Linear projection
We add an extra token as the {class} token
- Use of **1 D** Learnable Positional Embedding, on later analysis, they have some aspect of the  2 D shape
### Pre-Training
- Use of MLP with one hidden layer, GLUE non linearity
- Use of $z_l^0$
### Fine Tuning
- Attach a zero-initialized $D \times K$ feed-forward layer
- When images are of higher resolution
	- keep the patch size
	- sequence length becomes larger and positional embedding lose meaning
	- 2D interpolation of pre-trained positional embeddings
## Experimental Setups
- Hybrid: Feeding intermediate features extracted from a CNN
- Evaluated using few shots (when there are many examples to fine tune) and fine tune accuracy

# Observations from ViT layers
- CNN Filter like structures learned at the initial linear embedding layer
- Closer patches have similar positional embeddings
	- Form a 2D topology: the embeddings store information about their position in image
- Ability to attend to global information is used by the transformers from the start
# Conclusions
- To use ViT effectively, it requires a lot of data, as only then, will we not require the inductive bias.
- If not enough data is available CNN structures perform better
- ViT better performance/compute tradeoff, hybrids better at lower computational capabilities

https://www.youtube.com/watch?v=j3VNqtJUoz0&t=329s
https://github.com/labmlai/annotated_deep_learning_paper_implementations/blob/master/papers/vit.pdf
https://openaccess.thecvf.com/content/ICCV2021/html/Yuan_Tokens-to-Token_ViT_Training_Vision_Transformers_From_Scratch_on_ImageNet_ICCV_2021_paper.html?ref=https://githubhelp.com
https://openaccess.thecvf.com/content/CVPR2022/html/He_Masked_Autoencoders_Are_Scalable_Vision_Learners_CVPR_2022_paper