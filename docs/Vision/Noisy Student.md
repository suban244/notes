# Key idea
- Some mash of semi supervised learning, transfer learning
- We have a 
	- **Small dataset**: ImageNet with labels
	- **Much larger dataset**: Internet unlabeled
	- We wish to somehow use the much larger dataset.
- The unique approach is that instead of training on the unlabeled dataset for transfer learning, we use the labeled dataset and a teacher model
Teacher: Train a model on ImageNet and use it to label a large amount of unlabeled data
Student: Train on the new labeled data
- One would think Student **shouldn't** be able to outperform the teacher, but in this, the student outperforms the teacher
### Key Addition
- Add a lot of **noise**(augmentation) on the big dataset (added robustness) and a lot of **noise** on the model(dropout, stochastic depth)
- Student is larger than the teacher
 ![[Pasted image 20231225222716.png]]
# Some Details
- Teacher labels can be hard or soft pseudo labels. (Soft work better)
- Larger Teacher -> better
- A ton of data required
- Increase batch size of the student
- Teacher: gives pseudo labels to un-augmented images, Student: trained on augmented images
- Filter images the teacher model has low confidence on (probably they are out of domain images)
- Balance the unlabeled images class wise, so that they match the original distribution. (dublication: upsampling /talking images with higher confidence: downsampling)
- Iterative training
- Joint Training on labeled and unlabeled data.
- Training student from scratch maybe better
- All this introduces robustness to pertubations on the input images, better ability to tackle adversarial input