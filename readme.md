# EAST、CRNN实现OCR应用

### EAST网络
EAST网络主要是用于文字定位，详见论文[EAST: An Efficient and Accurate Scene Text Detector](https://arxiv.org/abs/1704.03155v2) 以及[Github](https://github.com/argman/EAST) 

这一部分源码实现是采用tensorflow，因此可以以EAST网络为基础来添加CRNN网络。

### CRNN网络

CRNN网络主要是用于文字识别，详见论文[An End-to-End Trainable Neural Network for Image-based Sequence Recognition and Its Application to Scene Text Recognition](https://arxiv.org/abs/1507.05717) 以及[Github项目](https://github.com/meijieru/crnn.pytorch) ，[模型训练方法](https://github.com/bgshih/crnn)

这一部分源码是采用pytorch，因此需要自己手动实现tensorflow版本，也是任务的主要难点之处。

### 文件说明

目前的Github文件主要是基于EAST的官方代码，助教提供的EAST代码略有不同(没有使用ResNet).其文件结构如下：

- /models
    - __crnn__ # 需要实现自己的crnn模型代码，需要重点实现
    - east # EAST官方代码，只不过调整了模型位置，可直接使用
	- resnet # EAST官方代码代码中实现时用到的resnet网络
- __/train_test__ # 两个模型单独训练测试,需要自己手动写
    - crnn_train.py # crnn模型的训练过程
	- crnn_test.py # crnn模型的测试过程
    - east_train.py # east模型的训练过程，可以直接使用官方代码
	- east_test.py # east模型的测试过程，可以直接使用官方代码
- __/run_demo_server.py__ #总体模型的实现(训练与测试)
- /OCR.pdf # 论文的一些总结

剩余的没有说明的文件，都是EAST官方代码的一部分。

除此之外，值得注意的一点是，将两个模型连接起来，需要注意两个网络的输入输出接口。因此可能需要__数据预处理__文件。

在EAST模型中，涉及到[Flask框架](http://flask.pocoo.org/) 以及 [tensorflow框架](http://www.tensorfly.cn/tfdoc/api_docs/index.html) 。
