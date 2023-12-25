https://huggingface.co/docs/transformers/tokenizer_summary
# Motivation
- Language keeps evolving continuously
- Mapping all words to OOV is bad
- Mapping different vectors of different versions of words can be wasteful
	- eat, eating, eated, ..
- Split words into sequences of known subwords.
a woman eats rice
t1 t2 t3 t4 t5 t6
a          wo ##man eat ##s rice
(0, 1)

# Description
- Model treats sub word as a token, split words not treated differently.
- Very long words
	- If the long word is not very common, *tough luck baby, natural selection (or stats)*
 - Also, we generally try to split words into the lowest amount of subwords
 - One could image with the word `watch` not being that common and `a` being super common, and the spitting `w##` `a##` `tch` is very bad
 - Read this for nepali: https://aclanthology.org/2022.sigul-1.14.pdf
 - Sentence Piece Embeddings: https://aclanthology.org/D18-2012.pdf#:~:text=SentencePiece%20implements%20the%20Decoder%20as%20an%20inverse%20operation,normalized%20text%20is%20preserved%20in%20the%20encoder%E2%80%99s%20output.
# Byte-Pair Encoding
- Start with characters and \[EOS\] token.
- Find common adjacent characters, combine it as a subword.
- Repeat until desired vocab size achieved.

# WordPiece
- Similarly to byte-pair
- Adds those pairs which maximize the likelihood of the training data
- *i think this means* Chooses the word that maximizes the equation, $l_1$ and $l_2$ are tokens  $$\frac {P(l_1l_2)} {P(l_2 | l_1)}$$ 
- used in [[BERT]]
# Unigram
- Starts with a large vocab and progressively trims down
- Removes ~10% of tokens that would least decrease loss, each iteration.
- stores probablities of each token, and tokenizes to maximize the probablity.
- Used in conjunction with sentence piece
# SentencePiece
- Takes the entire stream as input, including spaces, and uses BPE or unigram to construct vocab.
- Eg: albert, T5, ..
### Random Examples
- `---------------`: Tables idk
- `Tastyyyyyyyyyy`, `talbe` (misspelling)

- kina mbert le ramro gardaina 
- Muril and mbert

- Bayes rule for finding which is good, 