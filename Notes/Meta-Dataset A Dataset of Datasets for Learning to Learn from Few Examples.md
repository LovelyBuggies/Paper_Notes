# Reading Report

---

### Highlights

Few-shot classification refers to learning a classifier for new classes given only a few examples of them. While a plethora of models have emerged to tackle this recently, The paper finds the current procedure and datasets that are used to systematically assess progress in this task lacking. To address this, The paper proposes META-DATASET: a new benchmark for training and evaluating few-shot classifiers that is large-scale, consists of multiple datasets, and presents more natural and realistic tasks. The aim is to measure the ability of state-of-the-art models to leverage diverse sources of data to achieve higher generalization, and to evaluate that generalization ability in a more challenging and realistic setting. The paper additionally measures robustness to variations in the number of available examples and the number of classes.

---

### What is the problem to be tackled?

Since the tagging data in the data classification is very rare and the classification samples are few, few-shot learning is very popular. However, the current procedure and datasets that are used to systematically assess progress in few-shot learning is lacking.

Previous benchmarks for training and evaluating few-shot classifiers can not effectively evaluate how well meta-learners actually perform. Notably, generalization is only examined between different classes of the same dataset, but not different datasets, which is very constrained compared to the ultimate goal of few-shot learning "in the wild" where different distributions are encountered. Few-shot classification aims to classify unseen examples into one of N new classes, given only a few reference examples of each new class. 

---

### What is the difficulty to solve the problem?

1. To efficiently leveraging other training data towards this goal, albeit originating from different classes.
2. Without igonring relationships between categories when categorizing.

---

### How is the problem solved in the paper?

By establishing a metadata set that includes large data sets for many different data sets as a new evaluation benchmark for training and evaluating a small number of learning classifiers for multiple data sets. Sampled from it when the paper uses it, and the number of dataset categories in the sample and the distribution of each category's data are quite different. And some categores or the whole dataset are kept compltetely used to test the generalization abitity of classifiers. In short, try the best to imitate the datasets' situation in read-world.

According the approaches to few-shot learning, There are two ways and five models for trainging and testing, as follows:

1. **Non-incidental method**: First train a ConvNet classifier to predict all classes using standard batch training and treat the ConvNet until the penultimate layer as an embedding function g(x). Then the paper can use g and one of the follow methods to preidct classes and classify test sets:
   1. **"K-NN" baseline**: perform nearest neighbour lookup in that embedding space
   2. **"Finetune" baseline**: Train the classifier base on g and the new classes of the test sets. Then classify test sets by the adpoted classifier.
2. **Episode model**: Tried three popular plot models: Matching Networks, Prototypical Networks, and Model Agnostic Meta-Learning. All of them can train those ifferentiably-parameterized conditional distribution end-to-end via gradient descent. But different models are distinguished by the manner in which this conditioning on the support set is realized.
   1. **Matching Networks**: use then simplest method: train the model by weighted linear combination of the support labels.
   2. **Prototypical Networks**: construct a prototype for each class and accelerate in the direction of strong gradient continuity by using those prototype.
   3. **MAML**: uses the support set to perform a small number of training steps for adapting the classifier's weights to the new classes and then predicts the class distribution for query examples using the adapted weights

And it is a comparative experiment, using a single data set or multiple data sets to learn, and then compare.

---

### What is the novelty in the paper, particularly in methodology?

The most significant novelty in the paper is that the authors propose META-DATASET as a new few-shot classification benchmark, which offers a more realistic environment for assessing few-shot learning performance on a more realistic version of the task.

Their approach is twofold: 

1. changing the data

2. changing the formulation of the task.

First, the data they propose to use is much larger in size than any previous benchmark, and is comprised of multiple different existing datasets. This allows to examine a more challenging generalization problem, to new datasets altogether. Specifically, META-DATASET leverages data from the following 10 datasets: ILSVRC-2012 (ImageNet), Omniglot, Aircraft, CUB-200-2011 (Birds), Describable Textures, Quick Draw, Fungi1, VGG Flower, Traffic Signs, and MSCOCO. However, to ensure that episodes correspond to realistic classification problems, all episodes generated in META-DATASET use classes from a single dataset at a time only. Two of these datasets, Traffic Signs and MSCOCO, are fully reserved for evaluation, meaning that no classes from them participate in the training set. The remaining ones contribute some classes to each of training, validation and test splits of classes.

Second, they modify the task formulation by introducing a new sampling procedure for episodes that more closely resembles realistic learning scenarios. Contrary to the usual setup, they vary the number of classes and training sizes of different episodes. Further, within a given episode, the “shot” varies from class to class, introducing imbalance. To obtain realistic imbalance ratios, they sample the
number of examples of each class from a distribution derived from the relative class frequencies in the overall dataset.

---

### What are the significant experimental results?

In order to verify how much improvement can META-DATASET make on training and evaluating meta-learners, they experiment with five different models trained on different datasets and evaluated on META-DATASET. The five different models includes two non-episodic baselines ("K-NN" baseline and "finetune" baseline), and three popular episodic models(Matching Networks, Prototypical Networks and Model Agnostic Meta-Learning (MAML). 

The experiments consist of two parts. They evaluate results on META-DATASET using the five models trained on ILSVRC-2012 only in the first part and using the five models trained on all datasets in the second part.  

The experiment results demonstrate the competency of meta-learners for few-shot classification across different datasets compared to the two standard baselines. Notably, the Prototypical Network model performs consistently well. In general all models' performance improves when the way decreases and the shot increases. Finally, the models' ability to leverage data of diverse sources are assessed by comparing the values and from the visualization of the same data. They do not always observe an improvement from training on all datasets over training on ILSVRC-2012 only, which suggests that this direction requires further research. 

---

### What are the advantages and disadvantages of the method / solution proposed in the paper?

The advantage of META-DATASET is that it offers a new large-scale, diverse and realistic environment for training and testing meta-learners for the task of few-shot classification. However, experiment results show that the preliminary results do not always demonstrate a gain from training on all datasets as opposed to training only on ILSVRC-2012.

---

### How can the proposed method be further develop?

A direction that evidently requires further research is how to better leverage data from multiple sources at training time, which may make much improvement on performance of meta-learners.

---