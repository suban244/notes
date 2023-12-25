## Input Representation
- Positional Embeddings
- Segment Embeddings
	- `Sentence A` & `Sentence B`
- Token Embeddings 
	- WordPiece splitting ([[Subword Tokenization]])
	- BARD: 30K  wordpiece embeddings
# Hacker's Guide To Language Models
https://www.youtube.com/watch?v=jkrNMKz9pWU
- Language modeling -> Compression
- LM pre-training -> LM fine-tuning -> Classifier Fine-tuning
- When it comes to fine tuning, use of dataset like OpenOrca: 
	- "Question: ...? Answer: "
	-  Then the model does the next word prediction
	- Classifier Fine-Tuning: RLHF and friends
# Fine Tuning Procedure
![[Pasted image 20231204202943.png]]
# Large Language Models
- Obtaining a base model
- Compressing the information into a file. (lossy compression)
	- **For Llama 2 70B**: 
		- ~10TB  
		- 6,000 GPUs for 12 Days ($2M)
		- ~140GB File
	- For things like bard, 10x more computationally complex
- Trained Using [[Next Word Prediction]] 
- Can combine information from multiple sources.
## Assistant Models
- Query/Answer kind of models
- Optimization task stays the same, Swap out the dataset
- Hire people to make the data: ~100K conversations.
- Quality > Quantity
- Model able to access the knowledge of the pre-training phase, while keeping the structure of fine-tuning stage (alignment)
![[Pasted image 20231204092209.png]]
## Comparasion Label
- The third stage, Reinforcement Learning with Human Feedback (RLHF)
- Choosing which output of language model is better

# [[BERT]]

# Some language models
#### Roberta
- More data good
- More compute good
#### XLNET
- Relative positional embedding
	- How much should `dog` attend to previous word?
	- Generalizes better to long sequences
- Permutation Language Model
	- Instead of left to write, permute the sentence and do a sort of next word prediction on that
	- Equavalent to masking, but more predictions per sentencePermutation Language Modeell
	- Instead of left to write, permute the permute the sentence and do a sort of next word prediction on that
	- Equivalent to masking, but more predictions per sentence
#### ALBERT
- Parameter sharing
	- ![[Pasted image 20231204211504.png]]
	 - Less over-fitting when fine-tuning
- Cross Layer parameter sharing
	- Share all parameters between transformer layers
- ALBERT light in terms of parameters, but not speed
#### T5
- Exploring limits of transformers
- big model 11B
- All that matters is making model bigger, and more clean data
#### Electra
![[Pasted image 20231204212135.png]]
# Distillation
- Model Compression
- Train `Teacher`: use the best techniques to get the best model ( pre-training + fine tuning)
- Label a large amount of data using the `Teacher`
- Train `Student`: Train a smaller model (x50 smaller) to mimic Teacher output
- Mean Square / Cross Entropy
### Why does this work?
- Language models are like the **Ultimate Model**, and any other fine tuned model will only use a subset of the abilities of the LM
- Thus the distilled model only has the features relevant to the task
- How does distilation work with search??


bard to token replacement??