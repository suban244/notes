# Next Sentence Prediction
- Say you are trying to predict using next word prediction in a wiki article about a person X. 
- Now you will need to know about when person born, what they did, and so on.
- For learning relationship between sentences, using sentences from same document and different documents
# Masked Language Model
- Mask `k%` of input words
`This is a [MASK] sentence. This is a bad [MASK].`
- **Issue**
	- Low Number of predictions per sentence
	- Too little masking: too expensive to train
	- Too much masking: not enough context
## Masked Token Prediction: 
- Lower number of predictions compared to next word prediction
##  Next word Prediction
- Only uses left context(or right context) but Language understanding is bidirectional 
- Issue: words can "see themselves" in a bidirectional context
![[Pasted image 20231204184928.png]]
![[Pasted image 20231204204200.png]]
![[Pasted image 20231204204303.png]]
- Masked LM takes longer to converge but does much better pretty fast
- At the very beginning, left-to-right does better, probably because more data