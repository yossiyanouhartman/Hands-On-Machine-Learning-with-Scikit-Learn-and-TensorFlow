

# Chapter 2
[Ch2. ML end-to-end project | notebook ](./CH2_end-to-end-ML-project.ipynb)


**What is stratified shuffling?** 

This is called stratified sampling: the population is divided into homogeneous
subgroups called strata, and the right number of instances
are sampled from each stratum to guarantee that the test 
set is representative of the overall population.



# Chapter 3

**What metrics do you need to compose a ROC Curve?**

```python
# Out of all positive items, how many of them are correctly labeled as positive.
TPR = sensitivity = recall = TP / (TP + FN) 

# Out of all negative items, how many of them are correctly labeled as negative.
TNR = specificity = TN / (TN + FP) 

# Out of all negative item, how many of them care incorrectly labeled as positive.
FPR = fallout = FP / (FP + TN) = 1 - specificity
```
\
**When do you use ROC-curve and when the PR-curve?**

As a rule of thumb, you should prefer the PR curve whenever 
the positive class is rare or when you care more about the false 
positives than the false negatives. Otherwise, use the ROC curve.

\
**Strategies to use binary classifiers for multiclass classification**

- One way to create a system that can classify the digit images into 10 classes (from 0 to 9) is to train 10 binary classifiers, one for each digit (a 0-detector, a 1-detector, a 2-detector, and so on). Then when you want to classify an image, you get the decision score from each classifier for that image and you select the class whose classifier outputs the highest score. This is called the one-versus-the-rest (OvR) strategy, or sometimes one-versus-all (OvA).
- Another strategy is to train a binary classifier for every pair of digits: one to distinguish 0s and 1s, another to distinguish 0s and 2s, another for 1s and 2s, and so on. This is called the one-versus-one (OvO) strategy. If there are N classes, you need to train N × (N – 1) / 2 classifiers. For the MNIST problem, this means training 45 binary classifiers! When you want to classify an image, you have to run the image through all 45 classifiers and see which class wins the most duels. The main advantage of OvO is that each classifier only needs to be trained on the part of the training set containing the two classes that it must distinguish.


