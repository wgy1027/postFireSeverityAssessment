![](https://latex.codecogs.com/gif.latex?\begin{aligned}j\\\\i\end{aligned})

![](https://latex.codecogs.com/gif.latex?\begin{aligned}\\hat{\mathbf{h}}_t,\mathbf{c}_t&=\\text{LSTM}(f'(\mathbf{x}),[\mathbf{h}_{t-1},\mathbf{r}_{t-1}],\mathbf{c}_{t-1})\\\\\mathbf{h}_t&=\\hat{\mathbf{h}}_t+f'(\mathbf{x})\\\\\mathbf{r}_{t-1}&=\sum_{i=1}^ka(\mathbf{h}_{t-1},g(\mathbf{x}_i))g(\mathbf{x}_i)\end{aligned})

![](https://latex.codecogs.com/gif.latex?a(\mathbf{h}_{t-1},g(\mathbf{x}_i))&=\\text{softmax}(\mathbf{h}_{t-1}^{\\top}g(\mathbf{x}_i))=\frac{\exp(\mathbf{h}_{t-1}^{\\top}g(\mathbf{x}_i))}{\sum_{j=1}^k \exp(\mathbf{h}_{t-1}^{\\top}g(\mathbf{x}_j))}
  \end{aligned} %]]>

课题还是需要解决实际问题。我关心：（1）小样本问题；（2）样本不匀衡问题；（3）已有经验模型的迁移问题。

## Few-Shot Learning
few-shot learning比普通机器学习的不同之处是它可以利用前验知识。
Few-Shot Learning (FSL) is a type of machine learning problems (specified by emperience E, task T and performance measure P), where E contains only a limited number of examples with supervised information for the target T[[Wang, 2019](#Wang2019)].
FSL is applied in the following three typical scenarios:
- Acting as a test bed for learning like human. 
- Learning for rare cases. 
- Reducing data gathering effort and computational cost. 

Some algorithms related to Few-Shot Learning:
- Weakly supervised learning [163] learns from experience E containing only weak supervision (such as incomplete, inexact, inaccurate or noisy supervised information). 
- Imbalanced learning learns from experience E with a skewed distribution for y. 
- Transfer learning transfers knowledge from the source domain/task, where training data is abundant, to the target domain/task, where training data is scarce. 
-  Meta-learning improves the performance measure P of the new task T by the provided data set and the metaknowledge extracted across tasks by a meta-learner [[Hochreiter, 2001](#Hochreiter2001)].

A survey post about Meta-Learning:[Meta-Learning: Learning to Learn Fast](https://lilianweng.github.io/lil-log/2018/11/30/meta-learning.html)

Long Short Term Memory networks (LSTMs) are a special kind of RNN, capable of learning long-term dependencies. LSTMs were introduced by Hochreiter & Schmidhuber [[Hochreiter, 1997][#Hochreiter1997]]. Refer to the post by colah: [Understanding LSTM Networks](https://colah.github.io/posts/2015-08-Understanding-LSTMs/). Bidirectional LSTMs are an extension of traditional LSTMs that can improve model performance on sequence classification problems, providing additional context to the network and resulting in faster and even fuller learning on the problem, whitch is detailed in the post [How to Develop a Bidirectional LSTM For Sequence Classification in Python with Keras](https://machinelearningmastery.com/develop-bidirectional-lstm-sequence-classification-python-keras/#:~:text=Last%20Updated%20on%20January%208,LSTMs%20on%20the%20input%20sequence.).

### Matching Learing
- ![](http://latex.codecogs.com/gif.latex?g_\\theta(x_i,S)) uses a bidirectional LSTM to encode ![](http://latex.codecogs.com/gif.latex?x_i) in the context of the entire support set ![](http://latex.codecogs.com/gif.latex?S).
- ![](http://latex.codecogs.com/gif.latex?f_\\theta(x,S)) encodes the test sample ![](http://latex.codecogs.com/gif.latex?x) visa an LSTM with read attention over the support set ![](http://latex.codecogs.com/gif.latex?S).

1. First the test sample goes through a simple neural network, such as a CNN, to extract basic features, ![](http://latex.codecogs.com/gif.latex?f'(x)).

2. Then an LSTM is trained with a read attention vector over the support set as part of the hidden state:
![](https://latex.codecogs.com/gif.latex?\begin{aligned}ji\\ji\end{aligned})


![](http://latex.codecogs.com/gif.latex?\\begin{aligned}\\hat{\\mathbf{h}}_t, \\mathbf{c}_t &= \\text{LSTM}(f'(\\mathbf{x}), [\\mathbf{h}_{t-1}, \\mathbf{r}_{t-1}],\mathbf{c}_{t-1})\\\\  \\mathbf{h}_t &= \\hat{\\mathbf{h}}_t + f'(\\mathbf{x}) \\\\  \\mathbf{r}_{t-1} &= \\sum_{i=1}^k a(\\mathbf{h}_{t-1}, g(\\mathbf{x}_i)) g(\\mathbf{x}_i) \\\\
  a(\\mathbf{h}_{t-1}, g(\\mathbf{x}_i)) &= \\text{softmax}(\\mathbf{h}_{t-1}^\\top g(\\mathbf{x}_i)) = \\frac{\\exp(\\mathbf{h}_{t-1}^\\top g(\\mathbf{x}_i))}{\\sum_{j=1}^k \\exp(\\mathbf{h}_{t-1}^\\top g(\\mathbf{x}_j))}  \\end{aligned})

h^t,cthtrt−1a(ht−1,g(xi))=LSTM(f′(x),[ht−1,rt−1],ct−1)=h^t+f′(x)=∑i=1ka(ht−1,g(xi))g(xi)=softmax(h⊤t−1g(xi))=exp(h⊤t−1g(xi))∑kj=1exp(h⊤t−1g(xj))
Eventually f(x,S)=hK if we do K steps of “read”.

## Reference
<span id="Wang2019">[Wang2019] Wang, Yaqing, et al. "Generalizing from a few examples: A survey on few-shot learning." ACM Computing Surveys (CSUR) (2019).</span>
<span id="Hochreiter2001">[Hochreiter2001] S. Hochreiter, A. S. Younger, and P. R. Conwell. 2001. Learning to learn using gradient descent. In International Conference on Artificial Neural Networks. 87–94.</span>
<span id="Hochreiter1997">[Hochreiter1997] Hochreiter, Sepp, and Jürgen Schmidhuber. "Long short-term memory." Neural computation 9.8 (1997): 1735-1780.</span>






















