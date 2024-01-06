---
tags:
  - VLM
  - VLSM
  - natural-language-supervision
  - multimodal-learning
  - Vision-Transformers
  - zero-shot
---
[[CLIP]]-Driven Referring Image [[Segmentation]]
# Overview
[Vision Language Decoder](CRIS#Vision-Language-Decoder)
- Transfer fine grained semantic information from text to pixel level features(patches)
- Self-Attention: for long range dependencies
- Cross-Attention: for fine structured textual features to pixel level features
Text To Pixel [contrastive Learning](CRIS#Contrastive-Learning)
- Explicitly enforce the textual similarity
- Align language features with corresponding pixel features
# Architecture
![[Pasted image 20240106103205.png]]
## Feature-Extraction
- Image Encoder: Res-net
	- Use of 2nd-4th stage features
- Text Encoder: Standard encoder
	- $F_s$: `[CLS]` token
- Cross Modal Neck: incorporate the textual embedding into image features
- Use of [[CoordConv]]
## Vision-Language-Decoder
Takes input $F_v \in R^{N \times C}$ and $F_t \in R^{L \times C}$ generates multi-model features $F_c \in R^{N \times C}$. To capture positional information, *sine spacial positional embeddings* are added.
- Multi head self attention $$F^′_v = M HSA(LN (F_v)) + F_v$$
- Multi head cross attention $$ F^′_c = M HCA(LN (F^′_v), F_t) + F^′_v$$
- MLP block $$ F_c = MLP (LN (F^′_c)) + F ^′_c$$
## Contrastive-Learning
We get a $F_c \in R^{N \times C}$ from [vision language decoder](CRIS#Vision-Language-Decoder) and $F_s \in R^{C^{'}}$ from [text feature extractor](CRIS#Feature-Extraction).  We transform this by $$\large z_v = F^′_ cW_v + b_v, F^′_c = U p(F_c) $$$$\large z_t = F_sW_t + b_t,$$
- $z_t ∈ R^D$, $z_v ∈ R^{N×D}$ , $N = H/4 ×W/4$ 
- Up denotes 4× up-sampling
- Then it is trained constrastive style 