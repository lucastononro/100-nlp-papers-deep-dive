# Where to find it

The paper "Combining Labeled and Unlabeled Data with Co-Training" by Avrim Blum and Tom Mitchell explores a semi-supervised machine learning technique known as co-training, which leverages both labeled and unlabeled data to improve classification performance when labeled data is scarce. Co-training is especially useful when each data example has two distinct, sufficient views that can individually enable learning. In their paper, Blum and Mitchell propose and analyze a co-training algorithm that employs these two views, allowing two classifiers to "teach" each other by iteratively labeling new, unlabeled data.

Url: [Paper](https://www.cs.cmu.edu/~avrim/Papers/cotrain.pdf)

# Key takeaways

## Problem of Limited Labeled Data: 
 Labeled data is often costly and time-consuming to obtain, while unlabeled data is much easier to acquire.
 Co-training provides a way to use a large amount of unlabeled data to boost the performance of a classifier trained on a small labeled dataset.

## Two-View Assumption:
 Co-training assumes each example can be represented in two "views" (distinct feature sets) that independently provide enough information for classification. In their motivating example of web-page classification, they use (1) the words on the web page and (2) the words in hyperlinks pointing to the page as two views. The two views should be conditionally independent given the class label for co-training to work effectively.

## Co-Training Algorithm:

 1 - Initialization: Begin with a small set of labeled examples to train two classifiers separately on each view.

 2 - Iterative Process: Each classifier then labels a few of the most confidently predicted examples in the unlabeled pool.

 3 - Mutual Bootstrapping: The examples labeled by one classifier are used to augment the training set of the other, allowing each classifier to gradually improve.

## Theoretical Justification with PAC Analysis:
 Blum and Mitchell offer a PAC (Probably Approximately Correct) learning framework for co-training. Their analysis shows that, under certain conditions (e.g., conditional independence between views), unlabeled data can significantly reduce the labeled data needed for accurate classification. They also discuss how co-training can handle asymmetric classification noise.

## Empirical Results:
 The authors conducted experiments with real-world data on web-page classification, showing that co-training improved classification accuracy significantly compared to training on labeled data alone.


# Ideas and implementations

Potential for Weak Supervision and Self-Training: Co-training can be seen as a form of weak supervision, where initial weak classifiers bootstrap each other with unlabeled data. This approach could potentially integrate with other forms of weak supervision or active learning.

Reliability of Unlabeled Data Augmentation: The framework offers a robust way to systematically augment training with unlabeled data while managing the risk of introducing noise, making it appealing for real-world applications where labeled data is scarce and noisy.

