---
tags:
  - zero-shot
  - natural-language-supervision
  - multimodal-learning
  - Vision-Transformers
  - OpenAI
---
- Vision and Language representation
- [Zero shot classifier](CLIP#Zero-Shot)
	- Uses natural language as a flexible prediction space
- Two encoders: one for text and another for image(Resnet or [[ViT]])
	- contrastive learning
- Doesn't directly optimize for the benchmark

## Ingredients
- Data (400M text and image pairs)
- Contrastive pre-training
- Computational efficiency: transformers parallelism 
- Visual & Language Representation
## Why ?
- typical vision data creation is very labor intensive.
##  issues
- Scaling with higher compute
- abstract tasks like counting
- fine grained classification
	- Predicting the model of a car, species of a flower, etc
- Data not in the pre-training dataset
	- like MNIST: hand written digits
- some prompt engineering maybe required
- **NOT** Data efficient, but rather provides a method that can be scaled to supervise with millions of images.
## Zero-Shot
- Previously approaches to make it work in the embedding space.
	- De-VISE
	- FAIR
# Applications
- An image search engine
- Discriminator for GANs