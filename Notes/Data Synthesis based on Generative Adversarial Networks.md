# Reading Report

---

### Highlights

Privacy is an important concern for our society where sharing data with partners or releasing data to the public is a frequent occurrence. To address privacy leakage challenges, the paper proposes **table-GAN** to synthesize fake tables that are statistically similar to the original table yet do not incur information leakage. It shows that the machine learning models trained using their synthetic tables exhibit performance that is similar to that of models trained using the original table for unknown testing cases. Extensive experiments prove that only their method consistently shows the balance between privacy level and model compatibility.

---

### What is the problem to be tackled?

The paper is going to tackle the privacy leakage issues of **anonymization techniques** in data sharing scenario. Specially, it is very difficult to simultaneously achieve good privacy and usability levels after anonymization or other modifications. In general, privacy level and data utility are inversely proportional to each other. Moreover, even though re-identification attack and attribute disclosure are prevented, it is useless if membership attacks (*i.e.*, inferring about training samples by observing outputs from machine learning models ) can be done with high accuracy.

---

### What is the difficulty to solve the problem?

The challenges the paper is facing can be briefly summarized as follows: 

- Some sensitive attributes are often **disclosed** without any modification; 
- Data **usability** is negatively impacted after modifications;
- **New attacking methods** have been developed to recognize and remove noise.

---

### How is the problem solved in the paper?

The authors propose a **data synthesis method** based on generative adversarial networks (**GAN**s). The table-GAN consists of three neural networks (generator, discriminator, and classifier neural networks). The discriminator attempts to distinguish between real and synthetic records, and the generator obfuscates the task of the discriminator by generating realistic records. They continue iterating the adversarial game, and the generator can achieve unprecedented generation performance at the end of the two-player game. In the table-GAN, they add an additional classifier neural network to increase the semantic integrity of synthetic records. For instance, (cholesterol=60.1, diabetes=1) is not a semantically correct record (because the cholesterol level is too low to be diagnosed as diabetes), and there may be no such record in the original table. We prevent the generation of such records by adding a classifier into the training process because otherwise it is easy to determine that the table is fabricated.

The workflow of their study is listed as the following;

1. Records in the original table are converted into square matrix form; if needed, we pad with zeros.
2. The proposed table-GAN is trained using the converted square matrices;
3. The table-GAN generates many synthetic square matrices that will be converted and merged into a table.
4. The generated fake table is shared with partners who will perform analyses and design machine learning models.
5. The machine learning model trained using the synthetic table should be able to replace the model trained using the original table.

![workflow](https://i.loli.net/2019/06/02/5cf392275d4d921037.png)

Deeping into the network, they have three components: the `discriminator`, `generator`, and `classifier`, respectively. 

- The `classifier` is omitted because of space limitations, and it has the same neural network architecture as the `discriminator`. 
- The `generator` performs a series of deconvolution operations to generate a record. The final loss after the sigmoid activation can be back-propagated to the generator. 
- The dimensions of the latent vector input $z$ and intermediate tensors should be configured considering the number of attributes.

![NN architectur](https://i.loli.net/2019/06/02/5cf392e68867a47715.png)

The paper adopts one loss function from DCGAN and designs two more loss functions as follows:
- The `original loss` is adopted from DCGAN and was already shown in Equation 1.
- The `information loss` is defined as the discrepancy between two statistics of synthetic and real records.
- The `classification loss` is defined as the discrepancy between the predicted label by the classifier and the synthesized label. 

The overall procedure of the customized membership attack method. Its key step is to create a shadow table-GAN, a replica of the target table-GAN that the attacker wants to attack.

![overall procedure](https://i.loli.net/2019/06/02/5cf393d4717dc32933.png)

---

### What is the novelty in the paper, particularly in methodology?

1. Using GAN to generate identifiers for security issues in data sharing scenario;
2. No attribute values can be disclosed, providing a safer plan for data sharing;
3. Applying machine learning techniques to cryptography;
4. New-designed loss functions for table-GAN training.

---

### What are the significant experimental results?

- As for **data utility**, table-GAN with the low-privacy setting shows very high-quality synthesis performance. Specially,
  - It produces a more realistic cumulative distribution and a wider range of values than others;
  - It shows very good synthesis quality.
- As for **privacy evaluation**, the table-GAN shows relatively great model compatibility.
  - It shows the second-best model compatibility with very small differences;
  - It shows practically meaningful model compatibility in this dataset;
  - Table-GAN shows very stable average and standard deviation values concerning the distance to the closest record;
  - It has no one-to-one relationship between the original and generated tables.
  - It is observed that the performance does not greatly depend on classes.

---

### What are the advantages and disadvantages of the method/solution proposed in the paper?

 Some **advantages** of this work:

1. No one-to-one relationship is between real records and synthetic records, avoiding the re-identification;
2. Machine learning models trained using very carefully synthesized tables show behaviour similar to that of models trained using the original table;

Little **defects** exist in this work:

1. Limited for some other data types such as strings, system is not robust.
2. As we all know about neural network, GAN technology may have potential universal rules, which makes the system vulnerable;
3. The compatibility of this GAN is inferior to sdcMicro.
4. We don't think applying neural network which is difficult to describe abstract meaning to security problem is a suitable choice.

---

### How can the proposed method be further develop?

- Add some methods to increase the system compatibility.
- Improve system robustness by adding remedies for system failures.
- Extend the method to other data types such as strings and further improve the generation quality.
- We will further keep track of this novel model to see if it can apply to other domains.

---