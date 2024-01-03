# Relative-Positioning
- For fields where putting position doesn't make sense. Eg: Graphs
- Each token doesn't have one positional embedding, but rather $N$ positional embedding, for each token $N$.
![[Pasted image 20240103081246.png]]
![[Pasted image 20240103081427.png]]
Now adding the positional information to the token can be an issue, and each token as $N$ positional embedding. So we add this positional embedding information via the self-attention mechanism.
In the original paper, this information is added to the Values and the keys.
The exact values are learned.
- Also we may decide to clip the embedding at $k$ distance