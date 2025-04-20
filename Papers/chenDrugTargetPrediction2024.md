# (2024-02-29) Drug target prediction through deep learning functional representation of gene signatures

## 通过基因特征的深度学习功能表示进行药物靶标预测

|   |
|---|
|**作者:** Hao Chen; Frederick J. King; Bin Zhou; Yu Wang; Carter J. Canedy; Joel Hayashi; Yang Zhong; Max W. Chang; Lars Pache; Julian L. Wong; et al.|
|**期刊: Nature Communications （发表日期: 2024-02-29）**|
|**期刊分区:** ㅤㅤ ㅤㅤIF 14.7 ㅤㅤ ㅤㅤ ㅤㅤ ㅤㅤ ㅤㅤ ㅤㅤSCI Q1 ㅤㅤ ㅤㅤ ㅤㅤ ㅤㅤ ㅤㅤ ㅤㅤ中科院 综合性期刊1区 ㅤㅤ ㅤㅤ|
|**本地链接:** [Chen 等 - 2024 - Drug target prediction through deep learning functional representation of gene signatures.pdf](zotero://open-pdf/0_P5UT3AAI)|
|**DOI:** [10.1038/s41467-024-46089-y](https://doi.org/10.1038/s41467-024-46089-y)|
|**摘要:** _Abstract Many machine learning applications in bioinformatics currently rely on matching gene identities when analyzing input gene signatures and fail to take advantage of preexisting knowledge about gene functions. To further enable comparative analysis of OMICS datasets, including target deconvolution and mechanism of action studies, we develop an approach that represents gene signatures projected onto their biological functions, instead of their identities, similar to how the word2vec technique works in natural language processing. We develop the Functional Representation of Gene Signatures (FRoGS) approach by training a deep learning model and demonstrate that its application to the Broad Institute’s L1000 datasets results in more effective compound-target predictions than models based on gene identities alone. By integrating additional pharmacological activity data sources, FRoGS significantly increases the number of high-quality compound-target predictions relative to existing approaches, many of which are supported by in silico and/or experimental evidence. These results underscore the general utility of FRoGS in machine learning-based bioinformatics applications. Prediction networks pre-equipped with the knowledge of gene functions may help uncover new relationships among gene signatures acquired by large-scale OMICs studies on compounds, cell types, disease models, and patient cohorts._|
|**标签:**|
|**笔记日期:** 2024/10/25 16:36:28|

## 📜 研究核心

---

> Tips: 做了什么，解决了什么问题，创新点与不足？

### ⚙️ 内容

提出了FRoGS（Functional Representation of Gene Signatures）方法，将基因签名投影到到它们的生物功能而非身份上。这种方法类似于自然语言处理中的word2vec技术。将它运用到L1000数据集，能比仅基于基因特征的模型更有效预测化合物靶标。

### 💡 创新点

1、将NLP领域的word2vec转移到生物信息学中，并且将基因嵌入到表示多种生物信息的向量中。

2、FRoGS通过整合额外药理活性数据源，显著增加了高质量化合物-靶标预测的数量。

3、FRoGS方法能够捕捉基因签名之间的功能重叠，而不是仅仅基于基因身份的匹配，这在以往的研究中往往被忽视。

4、使用了一种Siamese neural network model(连体神经网络)，直接将FRoGS向量表示作为输入，直接计算化合物扰动和靶基因调控特征之间的相似性。

5、使用 FRoGS 向量作为编码基因或基因特征的起点，特定应用的模型训练所需的深度学习模型参数要少得多。

### 🧩 不足

基于基因表达水平的模型无法轻易区分靶标本身与其下游邻近蛋白，因为它们表现出相似的差异表达模式。这是所有基于转录的模型（包括我们的模型 L 和其他基于活性的模型）面临的共同挑战，也是造成靶标预测多药理学的原因之一。

未来的方向是扩大 FRoGS 框架的规模，利用图神经网络提取基因特征中的蛋白质-蛋白质相互作用（PPI）信号。

## 🔁 研究内容

---

### 💧 数据

L1000数据集、pQSAR compound activity matrix

### 👩🏻‍💻 方法

• 开发了FRoGS方法，通过深度学习模型训练，将基因签名映射到高维空间中的坐标，这些坐标编码了基因的生物功能。

• 使用了Siamese神经网络模型来计算化合物扰动和靶基因调控特征之间的相似性。

### 🔬 实验

### 📜 结论

FRoGS 在增强大规模数据集中基因特征的比较分析方面具有广泛的用途。

FRoGS召回率达到36.3%，在L1000数据集上表现出色。

通过 FRoGS 将基因特性转化为其功能作用，可以更容易地提取大规模数据中的微弱通路信号。

## 🤔 个人总结

---

> Tips: 你对哪些内容产生了疑问，你认为可以如何改进？

### 🙋‍♀️ 重点记录

### 📌 待解决

### 💭 思考启发