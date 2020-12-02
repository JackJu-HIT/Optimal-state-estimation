# Optimal-state-estimation
Optimal state estimation in robotics
本文来源于：https://zhuanlan.zhihu.com/p/37319831
                    
全文摘自西蒙教授的主页内容，google自动翻译。可能会有个别错误。英文OK，请看原文。Optimal State Estimation：Kalman，H-infinity，and Nonlinear Approaches，John Wiley＆Sons，2006。在过去的20年中，我学习了所有关于状态估计的知识，并将其写入本书。我喜欢一步一步的解释，所以这就是我写这本书的方式。我试图说清楚，但也包括最近的研究成果，所以它在既有技术和前沿研究方面有很好的平衡。它包括89个实例，176个书面练习和52个电脑练习。32个计算机例子的 Matlab代码可以从这个网站下载。该书有381篇参考文献，从20世纪20年代的历史参考文献到2006年发表的论文都有详细记录。

概观
教科书最佳状态估计基于我14年的行业经验和7年的学术研究经验。本书讨论了数学方法，以估计一般系统状态的最佳可能方式。虽然这本书完全以数学理论为基础，但所提出的方法都是以软件最终实现为目标。本文的目标是以尽可能最清晰但严谨的方式呈现状态估计理论，同时提供足够先进的材料和参考资料，以便读者准备为现有技术提供新的材料。工程师通常关心最终的实施，因此所提供的材料适用于离散时间系统。然而，为了完整性也讨论了连续时间系统，

至少有两个原因，工程师对状态估计很感兴趣。

1. 通常工程师需要估计系统状态以实现状态反馈控制器。例如，电气工程师需要估算电机的绕组电流以控制其位置。航天工程师需要估计卫星的姿态以控制其速度。经济学家需要估计经济增长以控制失业。医生需要估计血糖水平，以控制心脏和呼吸率。

2. 工程师经常需要估计系统状态，因为这些状态本身很有意思。例如，如果工程师想要测量工程系统的健康状况，则可能需要使用状态估计算法来估计系统的内部状况。工程师可能需要估计卫星位置，以便更加智能地安排未来的卫星活动。一位经济学家可能想要估计经济增长，以便提出一个政治观点。医生可能想估计血糖水平以评估患者的健康状况。

正如本书附录B所讨论的，还有许多关于状态估计的好书。这引出了一个问题：为什么还有关于状态估计主题的另一篇文章？本书的写作原因是为了提供其他状态估计书中没有的教学方法和观点。特别是希望本书能够提供以下内容。

1. 本书提供了一种直接的，自下而上的方法，帮助读者获得状态估计的清晰（但理论上严谨）的理解。这让人联想起格尔布的方法，该方法在过去几十年中已被证明对许多状态估计学生有效。然而，格尔布书的许多方面已经过时。此外，许多更新近的关于状态估计的书籍更像研究专着，并且不是普通工程专业学生完全可以访问的。因此需要本书。

2. 本书提供了简单的例子，为读者提供了理论的直观理解。许多书籍提出了状态估计理论，然后跟随需要计算机实现的例子或问题。但是，可以提供仅需要纸和铅笔来解决的简单示例和问题。这些简单的问题可以让学生更直接地看到理论在实践中如何运作。这再次让人想起格尔布的做法。

3. 本书提供了本网站提供的示例源代码（基于Matlab）。许多其他文本提供源代码，但它通常在磁盘或CD上，这使得代码易于过时。

4. 这本书提供了先进的主题在最佳状态估计的精心治疗。这些主题包括无迹滤波，高阶非线性滤波，粒子滤波，约束状态估计，降阶滤波，鲁棒卡尔曼滤波以及混合Kalman / H-infinity滤波。其中一些主题是成熟的，已经在20世纪60年代引入了，但其他主题是最新增加的最新技术。关于状态估计主题的其他书籍中的这种报道并不匹配。

还有其他关于状态估计的书籍提供了上述某些功能，但没有其他书籍提供所有这些功能。

本书分为四个部分：

1. 本书的第一部分包括介绍材料。

2. 本书的第二部分介绍卡尔曼滤波，它是状态估计的主力。

3. 本书的第三部分覆盖H-无穷滤波。

4. 本书的第四部分介绍非线性系统的滤波，包括无迹滤波和粒子滤波。

本书最后有三个简短的附录：

1. 附录A给出了卡尔曼滤波器发展的一些历史观点，从17世纪早期Roger Cotes的最小平方工作开始，并在20世纪60年代美国宇航局空间计划应用卡尔曼滤波结束。

2. 附录B讨论了许多其他关于卡尔曼滤波的书籍，包括他们独特的贡献。

3. 附录C 介绍了一些关于最佳状态估计和生命意义之间关系的哲学和宗教猜测（可在此获得John Wiley＆Sons的许可）。

勘误表
本书中的错误列表在http://academic.csuohio.edu/simond/estimation/errata.pdf。
解决手册
解决方案手册可以从出版商John Wiley＆Sons处获得。它包括了章节结尾处所有问题的解决方案，包括所有计算机练习的Matlab源代码。如果您是使用本书的课程教师，请直接与他们联系，他们会向您发送200页以上解决方案手册的免费副本。

反馈
我的电子邮件地址列于我的主页http://academic.csuohio.edu/simond/。我热烈欢迎您的反馈，意见，改进建议和更正。

教程和示例代码
要了解我的写作风格，您可以阅读我写过的一些关于卡尔曼滤波（pdf，425 KB），非线性拟合（pdf，227 KB）和H无限滤波（pdf，432 KB））。

文中例子的Matlab代码可以通过点击下面的链接下载：

Example 1.2 - MotorSim.m

Example 1.3 - LinearSimEx1.m

Example 3.5 - Chemical.m

Example 5.1 - DiscreteKFEx1.m

Example 5.2 - DiscreteKFAlt.m

Example 5.3 - DiscreteKFEx2.m, DiscreteKFEx2Plot.m

Example 7.1 - Correlated.m

Example 7.2 - Colored.m

Example 7.12 - KalmanConstrained.m

Example 8.4 - ContEx.m

Example 9.1 - FixPtSmooth.m

Example 9.2 - FixLagSmooth.m

Example 9.3 - FixIntSmooth.m

Example 10.1 - Multiple.m

Example 10.2 - Reduced.m

Example 10.3 - Schmidt.m

Example 10.4 - Robust.m

Example 11.2 - HinfEx1a.m, HinfEx1b.m

Example 11.3 - HinfContEx1a.m, HinfContEx1b.m

Example 12.1 - AddHinfEx1.m

Example 12.2 - AddHinfEx3.m

Example 12.3 - AddHinfConstr.m, AddHinfConstrMonte.m

Example 13.1 - MotorKalman.m

Example 13.2 - ExtendedBody.m, HybridBody.m

Example 13.3 - Hybrid2.m

Example 13.4 - Parameter.m

Example 14.1 - UnscentedEx.m

Example 14.2 - HybridUKF.m

Example 14.3 - HybridSimplex.m

Example 15.1 - ParticleEx1.m

Example 15.2 - ParticleEx2.m

Example 15.3 - ParticleEx3.m

Example 15.4 - ParticleEx4.m

Example 15.5 - ParticleEx5.m

Householder transformation software - House1.m

Modified Gram Schmidt software - MGS.m



Dan Simon, Professor
​
academic.csuohio.edu
图标
Department of Electrical and Computer Engineering

Cleveland State University
​
www.csuohio.edu
图标
Last Revised: March 24, 2015

Professor Simon's Home Page

Department of Electrical and Computer Engineering

Cleveland State University
