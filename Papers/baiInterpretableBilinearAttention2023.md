# (2023-02-02) Interpretable bilinear attention network with domain adaptation improves drug–target prediction

## 具有域适应能力的可解释双线性注意力网络改善了药物靶标预测

|   |
|---|
|**作者:** Peizhen Bai; Filip Miljković; Bino John; Haiping Lu;|
|**期刊: Nature Machine Intelligence （发表日期: 2023-02-02）**|
|**期刊分区:** ㅤㅤ ㅤㅤIF 18.8 ㅤㅤ ㅤㅤ ㅤㅤ ㅤㅤ ㅤㅤ ㅤㅤSCI Q1 ㅤㅤ ㅤㅤ ㅤㅤ ㅤㅤ ㅤㅤ ㅤㅤ中科院 工程技术1区 ㅤㅤ ㅤㅤ|
|**本地链接:** [Bai 等 - 2023 - Interpretable bilinear attention network with domain adaptation improves drug–target prediction.pdf](zotero://open-pdf/0_Q5LFPXN9)|
|**DOI:** [10.1038/s42256-022-00605-1](https://doi.org/10.1038/s42256-022-00605-1)|
|**摘要:**Predicting drug-target interaction is key for drug discovery. Recent deep learning-based methods show promising performance but two challenges remain: (i) how to explicitly model and learn local interactions between drugs and targets for better prediction and interpretation; (ii) how to generalize prediction performance on novel drug-target pairs from different distribution. In this work, we propose DrugBAN, a deep bilinear attention network (BAN) framework with domain adaptation to explicitly learn pair-wise local interactions between drugs and targets, and adapt on out-of-distribution data. DrugBAN works on drug molecular graphs and target protein sequences to perform prediction, with conditional domain adversarial learning to align learned interaction representations across different distributions for better generalization on novel drug-target pairs. Experiments on three benchmark datasets under both in-domain and cross-domain settings show that DrugBAN achieves the best overall performance against five state-of-the-art baselines. Moreover, visualizing the learned bilinear attention map provides interpretable insights from prediction results.|
|**标签:**|
|**笔记日期:** 2024/10/24 17:00:05|

## 📜 研究核心

---

> Tips: 做了什么，解决了什么问题，创新点与不足？

### ⚙️ 内容

提出DrugBAN框架，用来预测药物与靶标之间的相互作用（DTI）。DrugBAN通过双线性注意力网络（BAN）显式学习药物和靶标之间的局部相互作用，并通过领域适应技术提高在新领域（不同分布的数据）上的泛化能力。

### 💡 创新点

DrugBAN：一种深度双线性注意力网络(BAN)框架，具有域适应功能，可明确学习药物和目标之间的成对局部相互作用，并适应分布外数据。它基于药物分子图和靶蛋白序列进行预测，通过条件域对抗学习来对齐不同分布中学习到的相互作用表示，以便更好地概括新的药物靶点对。

(i) 通过双线性注意力机制捕获药物和目标之间成对的局部相互作用

(ii) 通过对抗域适应方法增强跨域泛化

(iii) 通过双线性注意力权重而不是黑盒结果给出可解释的预测。

CDAN：将对抗网络与多线性调节相结合，用于可转移的表征学习

### 🧩 不足

并没有考虑到3D结构的蛋白质，只考虑了1D和2D的蛋白质。

## 🔁 研究内容

---

### 💧 数据

三个公共DTI数据集：BindingDB、BioSNAP和Human。

### 👩🏻‍💻 方法

1、首先通过图卷积网络GCN和卷积神经网络CNN分别对2D药物分子图和1D蛋白质序列中的局部结构进行编码。

2、然后，将编码的局部表示输入到BAN成对的交互模块来学习这些药物和蛋白质表示之间的局部相互作用。用一个全连接层对局部联合表示进行解码以进行DTI预测，同时利用成对双线性注意力图来可视化每个子结构对最终预测结果的贡献，以提高可解释性。

3、对于跨域预测，使用条件域对抗网络（CDAN）将学习的知识从源域转移到目标域以增强跨域泛化。

### 🔬 实验

在BindingDB、BioSNAP和Human这三个公共数据集上测试分类性能，包括 In-domain 和 Cross-domain 。通过AUROC、AUPRC、Accuracy、Sensitivity、Specificity对模型进行评估。

还进行了消融实验

### 📜 结论

在域内DTI预测中，数据驱动的表示学习可以捕获更多重要的信息。DrugBAN还可以通过交互模块捕获交互模式

DrugBAN在泛化领域预测性能有很强的优势。

双线性注意力是捕获 DTI 预测交互信息的最有效方法。

DrugBAN在域内和跨域设置中始终实现了改进 DTI 预测性能。

DrugBAN还对预测结果提供了可解释性。

## 🤔 个人总结

---

> Tips: 你对哪些内容产生了疑问，你认为可以如何改进？

### 🙋‍♀️ 重点记录

In-domain classification assumes the testing data to be in the same domain as of the training data. Cross-Domain classification is a paradigm where testing data is from a different but related domain to the training data.

域内分类假设测试数据与训练数据属于同一域。跨域分类是指测试数据与训练数据来自不同但相关的领域。

### 📌 待解决

DeepMind的AlphaFold在蛋白质3D结构预测中取得了巨大进展，这一进展为在基于化学基因组学的 DTI 预测中利用 3D 结构信息打开了大门。将DrugBAN和这些数据集结合是未来一个很好的研究方向。

### 💭 思考启发