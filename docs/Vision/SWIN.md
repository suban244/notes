---
tags:
  - Vision-Transformers
---
A [Vision Transformer](VisionTransformers(VIT)) with a hierarchical structure.
- Starts with smaller patches $(4\times4\times3)$
- Patches are [merged](SWIN#Merging-Layer) to form bigger patches
**Linearly scaling** [Shifted Window](SWIN#Shifted-Window) attention mechanism
For tasks where you need a more granular input to transformer. Goal of using Transformer-based models as a general purpose **vision backbone**.
# Why ?
- The fixed transformer token size is not suitable for images where elements can vary in sizes
- For tasks like segmentation, we need more dense prediction
- Attention mechanism has a quadratic cost.
# Architectural Overview
![[Pasted image 20240102084630.png]]
- Start with patches of $4 \times 4 \times 3 = 48$, which is then linearly transformed to a size of $C$. Basically $d_{model}$.
### Positional Embedding
- Relative positioning works better.
## Attention Mechanism
Linearly scaling attention mechanism is achieved by limiting the attention to a non overlapping window.
### Shifted-Window
The widow for self attention is shifted in consecutive self attention layers.
Attention span is limited to a *non overlapping window*. The window is then shifted across the main diagonal, downwards, allowing for *cross-window attention*.
![[Pasted image 20240102084159.png]]
## Merging-Layer
- Adjacent 4 patches are merged into one patch, in the image space.
- Information of 4 patches is merged into one, and this new patch has double the hidden representation.
$$\large 4 \times C \xrightarrow[\text{}]{\text{merge}} 4C \xrightarrow{linear} 2C$$
https://openaccess.thecvf.com/content/ICCV2021/html/Liu_Swin_Transformer_Hierarchical_Vision_Transformer_Using_Shifted_Windows_ICCV_2021_paper