## Reading Report



---

### About

**Paper title**: Improving image classifiers for small datasets by learning rate adaptations

**Author**: Sourav Mishra, Toshihiko Yamasaki, Hideaki Imaizumi.

**Journal**: arXiv:1903.10726v2

**Year**: 2019



---

### Summary

The paper introduces an effective combination of existing techniques to improve the performance of the classifier in terms of accuracy and training time. By dynamically adjusting the learning rate, they achieved two to ten times the near state-of-the-art communication acceleration on different model architectures. Finding it particularly useful in small datasets of relatively simple architecture where machine reasoning is less reliable, they further verified the method, demonstrating its feasibility by implementing it on an unbalanced diagnostic image corpus. In conclusion, although existing some defects, this method shares a great amounts of signifanct merits, which paves the way for further reaserches for dermatological diseases in the realm of medication.



---

### What is the problem to be tackled?

Image classification via deep learning has seen rapid improvements in the last few years, but there still remain some bottlenecks. Conventional methods of training models require a large amount of data, often augmented or imputed from the original  dataset to make it balanced. The phase of training also happens to be the longest task in the deep learning process. With the advent of cloud computing, much of the machine learning tasks have shifted to portals such as Amazon Web Services and Microsoft Azure. Larger architectures usually imply longer running tasks translating to higher billed costs. This is of paramount importance to research groups or startups working on limited time and nancial resources to deliver outcomes. Therefore, to alleviate this training performance bottltneck becomes more and more necessary.



---

### What is the difficulty to solve the problem?

The improvement of training time and accuracy cannot be solely attributed to the architectures alone. Learning paradigms such as newer loss functions, optimization methods such as Dropout, and DropBlock along with better preprocessing routines have contributed to higher accuracy. In order to alleviate the training performance bottleneck, all these methods or technologies should be combined properly and may be creatively. 



---

### How is the problem solved in the paper?

In this paper, the authors have proposed an organic combination of existing techniques and some derivative ideas. focused on the hyper-parameter of learning rate. They allow it to adapt predictably over the training phase to improve time (measured as wall time) as well as accuracy (measured as validation accuracy).



##### **Initialization**

Firstly, they introduced an initial learning rate finder described by Smith et al to find a proper initial learning rate. The implementation used several mini-batches with gradually increasing values of learning rate, until the loss computed at end of each batch  started decreasing dramatically. Finding the rate of change of loss, so they could zero down to a good learning rate to begin.



##### **L2 Regulation**

Secondly, besides training the network with transforms similar to their baseline measurement, they employed L2 regularization and running a pass through their data to pre-compute activation values for the final layer, keeping all other layers frozen to retain the complex features from ImageNet training. What's more, rather than keeping the learning rate fixed from what was determined, they adopted Stochastic Gradient Descent with Restarts(SGD-R), where cosine rate annealing gradually decreased the learning rate over the epoch from a designated value to zero. The scheduling is governed as shown in Equation below:
$$
v_t = \frac{1}{2}(1 + vcos(\frac{t\pi}{T}))+v_{min}
$$
where v is the initial learning rate, t is the iteration over the epoch, and T is the total number of iterations to cover a epoch.



##### **Network Separation**

Thirdly, their final step in the optimization scheme was to unfreeze all the network layers, and use differential learning rates for separate sections of the networks. They saw the explaination of two related concepts with brevity:

- **Differential Leaning Rate(DLR)** involved the process of assigning thress separate learning rates, spanning the length of network & adhering to cosine rate annealing over the cycle length.
- **Cycle Length Multiplication(CLM)** involved extending the cosine annealing over progressively more integral number of epochs (with each subsequent cycle).



##### **Experiment Execution**

They assigned a very low-rate of a = 0:0001, left the initial layers virtually undisturbed, whereas a moderately high rate of a = 0:01 allowed elasticity for change in the higher layers. The mid-section of the CNN was assigned a rate of a = 0:001. Concurrent with changing the designated learning rates over dierent sections, they also extended the cycle length with a multiplication factor of 2.



---

### What is the novelty in the paper, particularly in methodology?

The novelty in the paper mainly reflects in two aspects: 

- Organic combination of existing techniques and some derivative ideas.
- Creative methods for learning rate adaptation.

They introduced the initial rate finder to determine most suitable initial learning rate, and employ L2 regularization and running a pass through their data to precompute activation values for the final layer, which promised performance advantages.

For learning rate adaptation, they adopted SGD-R where cosine rate annealing gradually decreased the learning rate over the epoch from a designated value to zero. Besides, in the final step of training, they employed DLR and CLM to gradually slow down the SGD-R process, which guaranteed a better convergence towards global minima.



---

### What are the significant experimental results?

This paper has mainly two results:

- Comparison with conventional method shows that proposed optimization scheme has shorter traing duration, especially for the complex neural net like DenseNet-161. This improvement, however, is at the expense of accuracy decrease with SGD-R. 

<p align="center">
<img src="https://ws1.sinaimg.cn/large/006tNc79ly1g1tugs9wfgj313e0gsjwd.jpg" alt="R1" title="ScoreChain" length = "1800" width="800"/><br/>
</p>

- Models tune to near state-of-the-art accuracy values, without a high training time and they are capable of learning without over-fitting, demonstrating that learning rate is effective tool. Also, larger architecture receive better performance gains than smaller ones, which is a valuable trait of our scheme.

<p align="center">
<img src="https://ws3.sinaimg.cn/bmiddle/006tNc79ly1g1tukka9gkj30ik0fu3zz.jpg" alt="R2" title="ScoreChain" length = "400" width="400"/><br/>
</p>


---

### What are the advantages and disadvantages of the method / solution proposed in the paper?



##### **Strengths**

- **High Scalability**: Attempting to reduce workload of the dermatologist by aiding faster screening & provide customized means to people for detecting possible skin problems, we believe that this method would also be useful for other medical areas.
- **High Reliability**: Performance comparison and confusion matrix show that this method is of particularly high reliability, illustrated by a relatively high accuracy, e.g. 84.90% for ResNet-152.
- **Low** **Cost**: Performance comparison and confusion matrix show that this method is of particularly high reliability, illustrated by a relatively economical traing duration, e.g. 946.14 for DenseNet-161.



**Weakness**

- **Disciplines Limitation**: This paper only show their models for medical use, what is performance upon other uses in diffirent disciplines? 
- **Data Scarcity**: This paper only show result with respect to one dermatological dataset, i.e. CIFAR-10, this somehow influence the dependability.
- **Lack Methods Comparison**: This paper have few comparison results, only comparison with a tradition method cannot fully supports its effectness, not sufficiently, if can. We expect they to compare their methods with more state-of-art Network.
- **Small Model Failure**: Although larger architecture receive better performance gains than smaller ones, which conform to the trend of development, we are still wonder why performance is relatively worse on small architecture.
- **Lack New NNs**: On our class, we contact with some other fantastic NNs, those, however is not present in this paper. We think add those new NNs must make the models more convincing.



---

### How can the proposed method be further develop?

- **Wider Exploration**: We expect to explore more uses of these models on different disciplines.
- **More Comprehensive Data**: We expect more comprehensive data from diversified datasets.
- **More Methods**: We expect more methods experiments, including their performances, analysis, as well as comparisons between them.
- **Small Model Enhancement**: We now today's tide of deeping learning is towards larger architectures, but there still exists needs for small ones. Therefore, it is of necessity to enhance the models for smaller ones.



---

