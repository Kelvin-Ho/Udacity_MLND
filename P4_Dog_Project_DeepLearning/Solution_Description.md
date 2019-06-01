# 解决方案简介
## 项目5：小狗识别

### 项目类型

深度学习（卷积神经网络） - 图像识别

### 任务

开发一个识别小狗的算法，如果输入一张小狗照片，可以判断该小狗的种类；如果输入一张人的照片，可以给出一个刚人脸最像的小狗品种。

### 数据集
包含训练、验证、测试集，每个数据集包含133个小狗种类的图片

### 方法和技术
- OpenCV的Haarcascades分类器
- ResNet50/VGG16预训练模型
- 框架：keras
- 神经网络结构：卷积层/池化层/全球平均池化层/dropout/全连接层
- 迁移学习(VGG, ResNet, Inception, Xception)

### 项目步骤

- 加载数据
	- 创建一个加载小狗数据集的函数
		- 加载小狗图片（包括训练集、验证集、测试集）
		- 加载函数使用sklearn.datasets的load_files(),其中**文件夹**名称作为标签
		- 函数返回标签和文件名，其中标签为'target'列，文件名为'filenames'列
	- 加载人脸数据，通过glob.glob查找所有匹配文件

- 人脸识别功能
	- 使用**OpenCV**的Haar cascade分类器检测人脸，导入cv2
	- 提取预训练的人脸检测器，使用cv2的cascade分类器
	- 加载人脸的BGR图像, cv2.imread()
	- 转换成灰度级, cv2.cvtColor()
	- 从图像中识别所有人脸,detectMultiScale()方法
	- 对所有人脸设置边界, cv2.rectangle()
	- BGR格式转换为RGB格式, cv2.cvtColor()
	- 显示RGB图像，plt.imshow()

- 小狗识别功能
	- 使用ResNet-50预训练模型检测小狗
	- 加载ResNet-50模型，从keras.applications.resnet50导入ResNet50
	- 定义ResNet-50模型，选择从'ImageNet'训练
	- 数据预处理（创建从路径转化为张量的函数）
		- 导入keras.prepocessing的image函数
		- 提取RGB图片，image.load_img()
		- 把图片格式转化成3维张量, image.img_to_array()，生成(length, width, 3)
		- 从3维张量转换为4维张量, (1,length, width, 3)
	- 创建ResNet50的预测函数
		- 返回图片的索引号，使用np.argmax()
	- 创建检测小狗函数
		- 从ImageNet的1000个种类中找到小狗相应的代号
		- 如果图像预测的代号在该范围内，则正确预测小狗

- 创建CNN对小狗分类（从头开始）

- 使用已有CNN对小狗分类
	- 数据预处理：使用已创建的函数从图像路径转化为张量，并进行归一化
	- 创建一个卷积神经网络，包括输入-卷积层-池化层-BN层-dropout层-全连接层-softmax函数返回概率
	- 从keras.layers导入各层，用sequential()初始化model
	- 训练模型 - 设置epoch、checkpoint、earlystopping
	- 导入最佳的模型权重
	- 预测（提取最大概率的结果的索引）

- 使用迁移学习的CNN对小狗进行分类
	- 选择一个已训练好的卷积神经网络，VGG16
	- 只增加了全球平均池化层和全连接层
	- 编译模型
	- 训练模型（设置checkpoint）
	- 导入最佳模型权重
	- 测试模型

- 使用迁移学习创建CNN对小狗进行分类：
	- 选择ResNet神经网络
	- 构造网络： 全球平均池化层 - BN层 - Dropout层 - 全连接层 - 激活层
	- 使用Adam优化器编译模型
	- 训练模型
	- 观察精度随epoch的变化，使用model.history读取训练集和验证集的精度，并可视化曲线
	- 导入最佳模型权重
	- 测试模型

- 总算法
	- 编写图像识别函数
	- 使用matplotlib.image的imread函数将输入图像转换为数组，结构为（M, N, 3)
	- 使用matplotlib.pyplot的imshow()函数显示图像
	- 使用前面的迁移学习创建的CNN预测图片
	- 如果是人脸，返回最接近该人脸的小狗种类；如果是小狗，返回预测小狗种类；如果都不是，返回“没有小狗和人脸”




