- U-net allowed for ability to customize exact architecture
- nnU-Net: A more focused approach to U-net, focus on aspects that make out the perfor-
mance and generalizability of a method
- Robust and Self adapting framework??

# Problem
- For sota performance, requirement of modification of arch of unet
- arch validation on (a lot of times) a single dataset.
- hard to validate superiority of arch, for the general case (across multiple datasets).

- arch tweeks can be shown to imporve performance for an unoptimized networks, but according to the paper, are unable to make results better for fully optimized one and push sota.
- 
## Medical Segmentation Decathlon
- participants asked to create a segmentation algorithm that generalizes across 10 datasets corresponding to different entities of the human body
- allowed to adapt to the dataset but must do so in an automated manner.
1) a development phase in which participants are given access to 7 datasets to optimize their approach on and, using their final and thus frozen method, must submit segmentations for the corresponding 7 held-out test sets. 
2) a second phase to evaluate the same exact method on 3 previously undisclosed datasets.
