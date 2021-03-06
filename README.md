In this assignment,we trained a CNN model to predict if a image has faces,i.e. face detection. 
And we implemented it using Mxnet,a open source deep learning frame. 
To detect the faces,the procedure is just as the following: 

1.bash --- $ ./buildDatabase.sh 

2.bash --- $ python train.py 

3.bash --- $ python detect_face.py 

Chinese Document 

为了实现人脸检测，培训了卷积神经网络模型，然后使用滑动窗口算法去检测原始图像中某一个区域是否含有人脸。 在这个任务中，我们使用了Mxnet框架，一个开源的、轻量级的深度学习框架。 

先介绍一下目录结构： 

buildDatabase.sh 根据原始数据构建适合Mxnet处理的数据形式 

data目录 存放原始数据集，data下一个文件夹为1类图片 

detect_face.py 检测单张图片中的人脸 im2rec.py Mxnet自带工具，构建mxnet可处理的数据集（详情移步mxnet） 

make_list.py 创建原始数据集清单文件（详情移步mxnet） predict 存放单张图片的由mxnet生成的数据信息 single 存放原始的单张图片 

train.py 模型培训 

使用方法： 

1.bash --- $ ./buildDatabase.sh 

2.bash --- $ python train.py 

3.bash --- $ python detect_face.py 

总体流程： 

1.自己准备好数据集 

2.使用mxnet自带的工具make_list.py im2rec.py 构建适合 mxnet处理的数据源 

3.使用mxnet的symbol搭建CNN，并进行模型培训 

4.采用滑动窗口算法将图像进行分割预测，选取预测度最高的图像局部区域作为人脸区域 

mxnet的一些参数说明： 

1.epoch:将所有数据让模型过一遍称为 一个 epoch 

2.batch:将一个epoch中的分为几次feed模型，一个feed为一个batch 

3.batch_size:一个batch中包含多少数据样本，称为batch_size 

4.num_batch:batch的数目 

5.num_epoch:epoch的数目 

6.epoch只在模型培训时出现，predict时不会出现 

7.使用不同的epoch，会让mxnet培训出不同的model 

说明： 1.此项目还存在诸多问题，譬如数据过拟合，涉及了大量的磁盘I/O操作，单张图片预测时间过长，并不能真实地进行人脸检测，所以为1.0版本，后面会进行大量的改进