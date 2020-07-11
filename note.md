

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

Long Short Term Memory networks (LSTMs) are a special kind of RNN, capable of learning long-term dependencies. LSTMs were introduced by Hochreiter & Schmidhuber [[Hochreiter, 1997](#Hochreiter1997)]. Refer to the post by colah: [Understanding LSTM Networks](https://colah.github.io/posts/2015-08-Understanding-LSTMs/). Bidirectional LSTMs are an extension of traditional LSTMs that can improve model performance on sequence classification problems, providing additional context to the network and resulting in faster and even fuller learning on the problem, whitch is detailed in the post [How to Develop a Bidirectional LSTM For Sequence Classification in Python with Keras](https://machinelearningmastery.com/develop-bidirectional-lstm-sequence-classification-python-keras/#:~:text=Last%20Updated%20on%20January%208,LSTMs%20on%20the%20input%20sequence.).

### Matching Learing
The task of Matching Networks [[Vinyals et al., 2016](#Vinyals2016)] is to learn a classifier ![](https://latex.codecogs.com/gif.latex?c_S) for any given (small) support set ![](https://latex.codecogs.com/gif.latex?S=\\{x_i,y_i\\}^k_{i=1}) (k-shot classification). This classifier defines a probability distribution over output labels ![](https://latex.codecogs.com/gif.latex?y) given a test example ![](https://latex.codecogs.com/gif.latex?\mathbf{x}). Similar to other metric-based models, the classifier output is defined as a sum of labels of support samples weighted by attention kernel ![](https://latex.codecogs.com/gif.latex?a(\mathbf{x},\mathbf{x}_i)) - which should be proportional to the similarity between ![](https://latex.codecogs.com/gif.latex?\mathbf{x}) and ![](https://latex.codecogs.com/gif.latex?\mathbf{x}_i).

<p align="center"><img align="center" width="500" src="https://lilianweng.github.io/lil-log/assets/images/matching-networks.png"></p>
Fig. The architecture of Matching Networks. (Image source: [[Vinyals et al., 2016](#Vinyals2016)])

![](https://latex.codecogs.com/gif.latex?c_S(\mathbf{x})=P(y\vert\mathbf{x},S)=\sum_{i=1}^ka(\mathbf{x},\mathbf{x}_i)y_i,\\,\\,\\text{where}S=\\{(\mathbf{x}_i,y_i)\\}_{i=1}^k)

where ![](https://latex.codecogs.com/gif.latex?x_i), ![](https://latex.codecogs.com/gif.latex?y_i) are the samples and labels from the support set ![](https://latex.codecogs.com/gif.latex?S=\\{x_i,y_i\\}^k_{i=1}), and a is an attention mechanism.

The attention kernel ![](https://latex.codecogs.com/gif.latex?a(\cdot,\cdot)) depends on two embedding functions, ![](https://latex.codecogs.com/gif.latex?f) and ![](https://latex.codecogs.com/gif.latex?g), for encoding the test sample and the support set samples respectively. The attention weight between two data points is the cosine similarity, ![](https://latex.codecogs.com/gif.latex?cosine(.)), between their embedding vectors, normalized by softmax:

![](https://latex.codecogs.com/gif.latex?a(\mathbf{x},\mathbf{x}_i)=\frac{\exp(\\text{cosine}(f(\mathbf{x}),g(\mathbf{x}_{i})))}{\sum_{j=1}^k\exp(\text{cosine}(f(\mathbf{x}),g(\mathbf{x}_j)))})

There are the following two kind of embedding functions:
(1) Simple Embedding

In the simple version, an embedding function is a neural network with a single data sample as input. Potentially we can set ![](https://latex.codecogs.com/gif.latex?f=g).

(2) Full Context Embeddings
The embedding function ![](https://latex.codecogs.com/gif.latex?f) for an example ![](https://latex.codecogs.com/gif.latex?\hat{x}) in the predictoin set (or query set) ![](https://latex.codecogs.com/gif.latex?B) is as follows:

![](https://latex.codecogs.com/gif.latex?f(\hat{x};S)=\\text{attLSTM}(f'(\hat{x});g(S);K))

where, ![](https://latex.codecogs.com/gif.latex?f') is a neural network (e.g., VGG or Inception networks), ![](https://latex.codecogs.com/gif.latex?K) is the number of processing steps in this embedding function ![](https://latex.codecogs.com/gif.latex?f). ![](https://latex.codecogs.com/gif.latex?g(S)) represents the embedding function ![](https://latex.codecogs.com/gif.latex?g) applied to each element ![](https://latex.codecogs.com/gif.latex?x_i) from the support set ![](https://latex.codecogs.com/gif.latex?S).

Its calculate steps is as following:
1. First the test sample goes through a simple neural network, such as a CNN, to extract basic features, ![](http://latex.codecogs.com/gif.latex?f'(x)).

2. Then an LSTM is trained with a read attention vector over the support set ![](https://latex.codecogs.com/gif.latex?S) as part of the hidden state:
![](https://latex.codecogs.com/gif.latex?\begin{aligned}\\hat{\mathbf{h}}_t,\mathbf{c}_t&=\\text{LSTM}(f'(\mathbf{x}),[\mathbf{h}_{t-1},\mathbf{r}_{t-1}],\mathbf{c}_{t-1})\\\\\mathbf{h}_t&=\\hat{\mathbf{h}}_t+f'(\mathbf{x})\\\\\mathbf{r}_{t-1}&=\sum_{i=1}^ka(\mathbf{h}_{t-1},g(\mathbf{x}_i))g(\mathbf{x}_i)\\\\a(\mathbf{h}_{t-1},g(\mathbf{x}_i))&=\\text{softmax}(\mathbf{h}_{t-1}^{\\top}g(\mathbf{x}_i))=\frac{\exp(\mathbf{h}_{t-1}^{\\top}g(\mathbf{x}_i))}{\sum_{j=1}^k\exp(\mathbf{h}_{t-1}^{\\top}g(\mathbf{x}_{\\top}))}\end{aligned})

3. Eventually ![](https://latex.codecogs.com/gif.latex?f_\\theta(\mathbf{x},S)=\mathbf{h}_K) if we do ![](https://latex.codecogs.com/gif.latex?K)  processing steps.

Noting that ![](https://latex.codecogs.com/gif.latex?a) is commonly referred to as a content based attention, and the above softmax normalizes ![](https://latex.codecogs.com/gif.latex?g(x_i)).

For the embedding function ![](https://latex.codecogs.com/gif.latex?g), we described the encoding function ![](https://latex.codecogs.com/gif.latex?g(x_i;S)) for the elements in the support set ![](https://latex.codecogs.com/gif.latex?S) as a bidirectional LSTM.

The above embedding method is called “Full Contextual Embeddings (FCE)”. Interestingly it does help improve the performance on a hard task (few-shot classification on mini ImageNet), but makes no difference on a simple task (Omniglot).

### Model-Agnostic Meta-Learning (MAML)
we consider a model represented by a parametrized function ![](https://latex.codecogs.com/gif.latex?f_\theta) with parameters ![](https://latex.codecogs.com/gif.latex?\theta). When adapting to a new task ![](https://latex.codecogs.com/gif.latex?T_i), the model’s parameters ![](https://latex.codecogs.com/gif.latex?\theta) become ![](https://latex.codecogs.com/gif.latex?\theta'_i). In our method, the updated parameter vector ![](https://latex.codecogs.com/gif.latex?\theta'_i) is computed using one or more gradient descent updates on task ![](https://latex.codecogs.com/gif.latex?T_i). For example, when using one gradient update,

![](https://latex.codecogs.com/gif.latex?\theta'_i=\theta-\alpha{j_\theta}L_{T_i}(f_\theta))

Where, the step size ![](https://latex.codecogs.com/gif.latex?\alpha) may be fixed as a hyperparameter or metalearned.

The model parameters are trained by optimizing for the performance of ![](https://latex.codecogs.com/gif.latex?f_{\theta'_i}) with respect to ![](https://latex.codecogs.com/gif.latex?\theta) across tasks sampled from ![](https://latex.codecogs.com/gif.latex?p(T)). More concretely, the meta-objective is as follows:

![](https://latex.codecogs.com/gif.latex?\underset{\theta}{\text{min}}\sum_{T_ip(T)}L_{T_i}(f_{\theta'_i})=\sum_{T_ip(T)}L_{T_i}(f_{\theta-\alpha{j_\theta}L_{T_i}(f_\theta)}))

Note that the meta-optimization is performed over the model parameters ![](https://latex.codecogs.com/gif.latex?\theta), whereas the objective is computed using the updated model parameters ![](https://latex.codecogs.com/gif.latex?\theta'). In effect, our proposed method aims to optimize the model parameters such that one or a small number of gradient steps on a new task will produce maximally effective behavior on that task.

The meta-optimization across tasks is performed via stochastic gradient descent (SGD), such that the model parameters ![](https://latex.codecogs.com/gif.latex?\theta) are updated as follows:

![](https://latex.codecogs.com/gif.latex?\theta\leftarrow\theta-\beta\nabla_{\theta}\sum_{\mathcal{T}_{i}\sim{p(\mathcal{T})}}\mathcal{L}_{\mathcal{T}_{i}}\left(f_{\theta_{i}^{\prime}}\right))

where ![](https://latex.codecogs.com/gif.latex?\beta) is the meta step size.

## Reference
<span id="Wang2019">[Wang2019] Wang, Yaqing, et al. "Generalizing from a few examples: A survey on few-shot learning." ACM Computing Surveys (CSUR) (2019).</span>

<span id="Hochreiter2001">[Hochreiter2001] S. Hochreiter, A. S. Younger, and P. R. Conwell. 2001. Learning to learn using gradient descent. In International Conference on Artificial Neural Networks. 87–94.</span>

<span id="Hochreiter1997">[Hochreiter1997] Hochreiter, Sepp, and Jürgen Schmidhuber. "Long short-term memory." Neural computation 9.8 (1997): 1735-1780.</span>

<span id="Vinyals2016">[Vinyals2016] Vinyals, Oriol, et al. "Matching networks for one shot learning." Advances in neural information processing systems. 2016.</span>






















