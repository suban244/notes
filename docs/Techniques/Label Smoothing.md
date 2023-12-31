- A type of regularization
- Change hard labels, one hot to smoother labels $\epsilon$ is small.
$$\large [0, 0, 1, 0] \rightarrow [\epsilon / 3, \epsilon / 3, 1 - \epsilon, \epsilon /3 ]$$

Because of softmax, we cannot really get an output that is one-hot encoded. 
But rather we push the model into learning (before activation) final layer output of the form $[-\infty, -\infty, \infty, -\infty]$  
- For this, weights become very large and this can cause model to over-fit
- We might need to change the loss function for this