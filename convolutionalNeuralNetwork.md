# 从零开始学习卷积神经网络的笔记（卷积神经网络篇）
我们在之前的文章已经介绍了关于神经网络的基础（假设成立的情况下），而卷积神经网络其实和更加经典的神经网络差不多，最大的差别就是所引入的卷积层，顾名思义，这一层的特色就是做卷积操作，所使用的卷积核自然不能是传统全连接层的那种模式，而是一个多维的线性处理算子（此维度与输入维度相同，否则无法完成卷积操作，对此有疑问的可以先往下看）。
## 卷积神经网络纪年史
+ Kunihiko Fukushima提出的Neocognitron模型[Fukushima and Miyake, 1982]：此神经认知机将一个视觉模式分解成许多子模式（特征），然后进入分层递阶式相连的特征平面进行处理，它试图将视觉系统模型化，使其能够在即使物体有位移或轻微变形的时候，也能完成识别。再往前追溯，可以认为这个模型的推出受到了1959年Hubel和Wiesel提出的感受视野的概念，当时的工作是对猫视觉皮层细胞的研究。
+ Yann Lecun在1998年正式提出了CNN模型（Lenet5），其本质还是一个多层感知机，重点在于所采用的局部连接和权值共享的方式规定了神经网络主要的进行方式。
+ 2012年，Imagenet图像识别大赛中，Hinton组的论文《ImageNet Classification with Deep Convolutional Neural Networks》中提到的Alexnet引入了全新的深层结构和dropout方法，一下子把error rate从25%以上提升到了15%，颠覆了图像识别领域。Alexnet有很多创新点，但现在看来是一项非常简陋的工作。他主要是让人们意识到原来那个福岛邦彦提出，Yann Lecun优化的Lenet结构是有很大改进空间的；只要通过一些方法能够加深这个网络到8层左右，让网络表达能力提升，就能得到出人意料的好结果。
+ 顺着Alexnet的思想，Lecun组2013年提出一个Dropconnect，把error rate提升到了11%。而NUS的颜水成组则提出了Network in Network，NIN的思想是CNN原来的结构是完全可变的，然后加入了一个1*1conv层，NIN的应用也得到了2014年Imagine另一个挑战——图像检测的冠军。Network in Network的思想是CNN结构可以大胆去变化，由此，Inception和VGG在2014年把网络加深到了20层左右，图像识别的error rate也大幅提升到6.7%，接近人类的5.1%。
+ 2015年，MSRA的任少卿、何凯明、孙剑等人，尝试把identity加入到神经网络中。最简单的Identity却出人意料的有效，直接使CNN能够深化到152层、1202层等，error rate也降到了3.6%。后来，ResNeXt, Residual-Attention，DenseNet，SENet等也各有贡献，各自引入了Group convolution，Attention，Dense connection，channelwise-attention等，最终Imagenet上error rate降到了2.2%，完爆人类。现在，即使手机上的神经网络，也能达到超过人类的水平。
+ 而另一个挑战——图像检测中，也是任少卿、何凯明、孙剑等优化了原先的R-CNN, fast R-CNN等通过其他方法提出region proposal,然后用CNN去判断是否是object的方法，提出了faster R-CNN。Faster R-CNN的主要贡献是使用和图像识别相同的CNN feature，发现那个feature不仅可以识别图片是什么东西，还可以用来识别图片在哪个位置！也就是说，CNN的feature非常有用，包含了大量的信息，可以同时用来做不同的task。这个创新一下子把图像检测的MAP也翻倍了。
+ 在短短的4年中，Imagenet图像检测的MAP从最初的0.22达到了最终的0.73。何凯明后来还提出了Mask R-CNN,给faster R-CNN又加了一个mask head。即使只在train中使用mask head，但mask head的信息传递回了原先的CNN feature中，因此使得原先的feature包含更精细的信息。由此，Mask R-CNN得到了更好的结果。
+ CNN结构越来越复杂，于是谷歌提出了Nasnet来自动用Reinforcement Learning 去search一个优化的结构。Nas是目前CV界一个主流的方向，自动寻找出最好的结构，以及给定参数数量/运算量下最好的结构（这样就可以应用于手机），是目前图像识别的发展方向。但何凯明前几天（2019年4月）又发表了一篇论文，表示其实random生成的网络连接结构只要按某些比较好的random方法，都会取得非常好的效果，比标准的好很多。Random和Nas哪个是真的正确的道路，这就有待研究了。
+ 具体的的可以参见一篇比较详细的[博客](https://www.jiqizhixin.com/articles/2019-05-27-4)

## 网络层及特点
### 预处理
+ 平均值归零处理（Mean-subtraction）
+ 归一化处理（Normalization）
+ PCA白化（PCA Whitening）
+ 局部归一化处理（Local Contrast Normalization）

### 卷积层


### 池化层
### 非线性
### 全连接层
### 反卷积层
### 感兴趣区域池化层
### 空间金字塔池化
### VLAD特征层
### 空间变化层