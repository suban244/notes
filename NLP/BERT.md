### Embeddings
- Word2Vec
#### ELMo: Context Matters
- words have different meaning depending on the context
- "stick": "let's stick to the plan" vs "i used a walking stick"
- Use of bidirectional LSTM to look at the whole context
- Trained on predicting the next word
![[Pasted image 20231206130331.png]]
![[Pasted image 20231206143007.png ]]
#### ULM-FiT
- Utilize a lot of what model learns during pretraining
- Introduces a way to do transfer learning
#### OpenAI Transformer
Decoder model for language modeling
- Stack 12 decoders and throw 7000 books at them
	- books good, long context
- Trained using next word prediction, forward only language model
	- Issue: Only context from one side
	- We need to mask the next token as to not let embedding leak in 
## BERT 
Encoder model for language modeling
![[Pasted image 20231206145026.png]]
### Masked Language model
![[Pasted image 20231206145153.png]] 
### Two sentence Task 
From this task, it is assumed that the bert model learns to encapsulate the entire information of a sentence in the `[CLS]` token
![[Pasted image 20231206145557.png]]
### BERT On different Tasks
![[Pasted image 20231206145641.png]]
### BERT as a feature extractor
![[Pasted image 20231206145941.png]]
![[Pasted image 20231206145954.png]]