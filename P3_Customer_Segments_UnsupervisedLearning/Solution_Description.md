# 解决方案简介
## 项目3: 创建用户分类

### 项目类型

非监督学习

### 任务

如何最好地描述一个批发商不同种类客户之间的差异，可使批发商更好地组织物流服务满足每个客户需求

### 数据集

来自UCI机器学习信息库，数据库是关于客户针对不同类型产品的年度采购额（用金额表示）

### 方法和技术

- 异常值定义方法：Turkey
- 决策树回归方法
- 散布矩阵：用于观察特征间的相关性
- 主成分分析（PCA）：用于减少数据集维数，同时保持对方差贡献最大的特征
- 聚类（K-means法或高斯混合模型法），聚类轮廓系数

### 项目步骤

- 加载数据
- 探索性数据分析
	- 选择样本观察数据，分别代表哪种客户？
	- 特征相关性分析，即一个特征能否被其他特征预测得到，并用决定系数评估
	- 结合散点矩阵观察特征间的相关性
- 数据预处理
	- 特征缩放。对于倾斜的数据，可用**Box-Cox变换**或者**对数变换**进行非线性缩放
	- 对1.5倍IQR以外的异常值进行移除
- 主成分分析
	- 使用sklearn.decomposition的PCA及transform方法将数据数据集转换到6成维度，并进行PCA结果可视化。[可视化代码](https://github.com/Kelvin-Ho/Udacity_MLND/blob/master/P3_Customer_Segments_UnsupervisedLearning/visuals.py)
	- 计算前几个主成分的方差总和，是否已经接近1
	- 在进行一次主成分分析，转换成2个维度，比较6维度和2维度的方差解释比
	- 对2维度主成分可视化，观察主成分的散点分布及初始特征的投影，理解每个每个特征与两个主成分的关联
- 聚类
	- 使用一种聚类方法，如果是Kmeans，导入sklearn.cluster;如果是高斯混合模型，导入sklearn.mixture
	- 计算聚类中心（采用平均值）
	- 预测数据集每一个点所属的簇
	- 计算平均轮廓系数，采用sklearn.metrics的silhouette_score
	- 尝试不同的聚类数，观察哪一个轮廓系数最大
	- 对最佳聚类方案进行可视化。[可视化代码](https://github.com/Kelvin-Ho/Udacity_MLND/blob/master/P3_Customer_Segments_UnsupervisedLearning/visuals.py)
	- 数据恢复，使用反向转换将聚类中心代表的类别恢复（使用PCA的inverse_transform方法）
- 结论
	非监督学习的聚类结果可以作为特征用于监督学习，提升模型预测能力





