
# Rossmann销售预测项目

### 项目使用的软件和库
- 软件：
    - Jupyter Notebook 5.5.0
    - python 3.6.5
- 库文件：
    - numpy 1.13.3
    - pandas 0.22.0
    - seaborn 0.8.1
    - matplotlib 2.2.2
    - XGBoost 0.82
    
### 机器硬件
- 处理器：Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
- 显卡： NVIDIA Quadro K1100M

### 机器操作系统
- Windows 7 Enterprise

### 项目文件说明
- 输入数据：data文件夹，train.csv, test.csv, store.csv。位于data文件夹中
- 输出数据：
-	prediction文件夹，包含每个模型对测试集的预测值，其中final.csv 是最终提交结果
-	valid_prediction文件夹，包含每个模型对验证集的预测值，用于模型融合优化
- 	tuning_output文件夹，包含调参的输出结果
- 相关代码和可视化：Rossmann_Project.ipynb
- 项目报告：Rossmann销售预测.pdf
    
### 程序运行说明
所有可视化及代码均在Rossmann_Project.ipynb文件中实现，按顺序运行如下：
- 导入数据集，进行数据评估
- 数据清洗
- 数据可视化
- 特征工程
- 建立模型（每次训练模型需要在特征工程板块选上相应特征并重新运行一次特征工程代码）
- 模型调参
- 模型融合
- 结果校正
- 最终结果可视化

模型运行时间：运行单个xgboost模型最快的需要0.5小时，最慢的需要1.5小时左右


