# 目录</br>

[一、前言](#1)<br>
[二、Softmax Regression](#2)<br>
[三、去噪自编码器](#3)<br>
[四、多层感知机](#4)<br>
[五、简单的卷积网络](#5)<br>

<h1 id='1'>前言</h1>

&nbsp;&nbsp;&nbsp;&nbsp;在这个人工智能盛行的时代，希望有更多的小伙伴和我一起，在这条路上分享各自的经验。也请大牛们多多关照，您的宝贵意见一定能促使我成为一名优秀的人工智能开发者。<br>

<h1 id='2'>Softmax Regression</h1>

* **输入层：** mnist手写数字识别训练集-28*28只有灰度的图片数据展开成一维的向量784</br>
* **隐含层：** 激活函数为Relu，权重w1，偏执b1</br>
* **输出层：** 结果为0-9的数字，长度为10的向量。权重w2，偏执b2</br>
* **损失函数：** 交叉熵</br>
* **其他：** 使用L2正则化防止过度拟合，学习速率平滑递减提高学习效率</br>

* **附**</br>

&nbsp;&nbsp;&nbsp;&nbsp;<a href="https://blog.csdn.net/u012162613/article/details/44261657">L12正则化：</a>就是为了让拟合函数的系数尽量小防止过度拟合，因为拟合函数需要照顾每一个训练集所以往往系数很多，通过正则化就可以让系数变小。在正则化后也会产生损失的，所以总的损失函数也需要加上该损失。</br>
&nbsp;&nbsp;&nbsp;&nbsp;<a href="https://blog.csdn.net/zchang81/article/details/70225220">tf.nn.softmax_cross_entropy_with_logits：</a>把softmax计算与cross entropy计算放到一起,提高计算效率。</br>
&nbsp;&nbsp;&nbsp;&nbsp;<a href="https://blog.csdn.net/zchang81/article/details/70225220">Sigmoid/Tanh/ReLU：</a>不同激活函数有各自的特定。</br>

<h1 id='3'>去噪自编码器</h1>

* **输入层：** 输入数据加上高斯噪音</br>
* **隐含层：** 激活函数为传入，权重w1，偏执b1。该节点数小于输入层节点数</br>
* **输出层：** 通过高阶特征重构源数据。权重w2，偏执b2</br>
* **损失函数：** 平方误差</br>

* **附**</br>

&nbsp;&nbsp;&nbsp;&nbsp;特点：希望输入与输出一致并且使用少量稀疏的高阶特征来重构自身。</br>
&nbsp;&nbsp;&nbsp;&nbsp;噪音：一般情况数据会加入噪音，在重复的学习后，无规律的噪音将被去除，这样我们就能从噪音中学习数据的特征。去噪自编码器中最常用的是<a href="https://blog.csdn.net/u012936765/article/details/53200918">加性高斯噪音自编码器</a>。</br>

<h1 id='4'>多层感知机</h1>

* **输入层：** mnist手写数字识别训练集-28*28只有灰度的图片数据展开成一维的向量784</br>
* **隐含层：** 激活函数relu，再按一定比例dropout</br>
* **输出层：** 使用softmax激活隐含层</br>
* **损失函数：** 交叉熵</br>

* **附**</br>

&nbsp;&nbsp;&nbsp;&nbsp;将一部分训练数据置为0，可避免在训练集上越来越精确，却在测试集上越来越差，整个网络使用dropout减轻过拟合，自适应学习速率Adagrad，Relu激活函数避免梯度弥散。</br>
&nbsp;&nbsp;&nbsp;&nbsp;Relu解决梯度弥散问题:用softmax函数时，在0附近函数梯度较大，而向两边越来越小，导致模型的训练中根据梯度更新权重时效率很低。而且Relu函数还有单侧抑制，稀疏激活等特点。</br>
&nbsp;&nbsp;&nbsp;&nbsp;Relu函数:<a href="https://www.zhihu.com/question/52020211?from=profile_question_card">单侧抑制性和稀疏激活性</a></br>
&nbsp;&nbsp;&nbsp;&nbsp;现在隐含层主要还是用Relu函数以及其变种（<a href="https://blog.csdn.net/u013146742/article/details/51986575">Leaky-ReLU、P-ReLU、R-ReLU等</a>）激活，对应输出层还是sigmoid函数，因为该函数在0-1，最接近概率分布</br>

<h1 id='5'>简单的卷积网络</h1>

* **输入层：** mnist手写数字识别训练集</br>
* **第一层卷积：** 卷积尺寸5*5，颜色1个通道，32个卷积核</br>
* **第二层卷积：** 卷积尺寸5*5，上层32核，64个卷积核</br>
* **隐含层：** 1024个节点，relu激活</br>
* **dropout层：** dropout系数0.5</br>
* **输出层：** 10个节点，softmax激活</br>
* **损失函数：** 交叉熵</br>
* **学习速率：** 1e-4，较小的学习速率</br>

* **附**</br>

&nbsp;&nbsp;&nbsp;&nbsp;<a href="https://blog.csdn.net/bea_tree/article/details/51376577">卷积网络</a>是一种前馈神经网络，它的人工神经元可以响应一部分覆盖范围内的周围单元，对于大型图像处理有出色表现。它包括卷积层(convolutional layer)和池化层(pooling layer)。</br>



