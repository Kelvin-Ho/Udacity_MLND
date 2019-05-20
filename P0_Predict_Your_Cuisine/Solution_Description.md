# 解决方案简介
## 项目0：预测你的下一道世界料理

### 项目类型

自然语言处理

### 任务

给定佐料名称，预测菜品所属的菜系

### 数据集

包含菜系及其佐料的单词

### 方法和技术

- nltk库：一个先进的用来处理自然语言数据的python程序
- re库：正则表达式
- TF-IDF: 用于信息检索与文本挖掘的常用加权技术。
	- tf(term frequency): 词频，只一个词语在文件中出现的频率
	- idf(inverse document frequency): 一个词语普遍重要性的度量

### 项目步骤

- 加载数据
- 单词清洗：去除单词单复数、时态等变化，去除标点符号
	- 使用re.sub()函数去除标点符号，保留a..z A..Z单词字符
	- 使用nltk.stem的WordNetLemmatizer去除单词单复数、时态保留单词词干
- 特征提取
	- 使用TF-IDF将菜品的佐料转换成数值特征向量
- 验证集划分
	- 调用train_test_split函数将数据集分为训练集和验证集
- 建立模型
	- 调用sklearn的逻辑回归模型
	- 从sklearn.model_selection导入GridSearchCV，自动搜索参数
	- 把输入变量和目标变量输入到模型
	- 从sklearn.metrics导入accuracy_score计算模型准确率
- 模型预测
	- 将模型对测试集进行预测




