Title: A Bayesian's View on Neural Nets
Subtitle: Deep Learning, Convolution and the Hype Machine
Date: 2018-10-23 10:20
Category: critique
Tags: critique, ds, advice, neuralnets, neural, deeeplearning, hype
Authors: Varun Nayyar

My first neural net was actually coded up in 2009. I had decided to go to med school and while hating the degree program, I got a chance to do an elective called "Science in Medicine". I didn't really know how to program at this point, so it was done in excel and I trained a neural net (really a perceptron with 2 input units and a sigmoid activation) to mimc and NAND gate. It is a little known fact that backprop is simple enough to implement in excel. Everyone was suitably impressed (if unsure of what they were seeing), and when I quit to take up a mathematics/engineering degree 6 months later, the signs were there. 


When I finally stopped dabbling in ML and started taking a more formal approach at the start of 2014, I did it primarily out of "Elements of Statistical Learning" by Hastie, Tibshirani and Friedmann. In the very first section on neural nets, this was the description they had given

> There has been a great deal of hype surrounding neural networks, making them seem magical and mysterious. As we make clear in this section, they are just non-linear statistical models, much like the projection pursuit regression model discussed above.

This had been published in 2009, a few years before [Alexnet](https://en.wikipedia.org/wiki/AlexNet) and GPU's burst on scene in 2012. As such, the neural nets in the textbook were small, the [relu](https://en.wikipedia.org/wiki/Rectifier_(neural_networks)) hadn't even made the cut in activation functions described, and convolutional neural nets were described in some detail, but without the word convolution (called constrained nets - which is arguably more accurate, they're less complex than dense layers and they're not even convolutions, they're cross correlations (which is a moot point given that the convolution is being learned so it doesn't matter anyway)). My lecturer had inherited the bias, and through him, I too considered that neural nets were nothing special. 

Of course, my friends from the comp sci department were obsessed with neural nets and anything that could use a neural net, and I think deep learning was slowly coming into use (and I applaud the nomenclature). At the time, I preferred bagging (primarily due to my fondness of non-parametric methods) which live on as random forests and even back then was a hipster in the machine learning space as boosting was the premier ensemble method. I chose to do Bayesian Stats and then mucked around a few different areas (GMMs, Symbolic Data, Approximate Bayesian Computations), all of which have had no bearing on my work since, but I am at least secure in [my mathematician's apology](https://en.wikipedia.org/wiki/A_Mathematician%27s_Apology).

I recently visited a NVIDIA conference, and despite the fact it was actually a sales pitch to managers and C level exec's masquerading as a machine learning conference, it did remove the last objections I had to neural nets (meeting the other ML guys was probably more helpful). The basic of the arguments was that the world is inherently non-linear and neural nets are the best way to capture that non-linearity. It wasn't perfect (and after all which model is), it might be discarded quite easily, but we're still doing linear regressions and they're still useful, and in all likelihood, neural nets aren't going anywhere in the near future.

## Hidden Complexity

I'm going to use the architecture [this blog](https://towardsdatascience.com/a-simple-2d-cnn-for-mnist-digit-recognition-a998dbc1e79a) to show what I mean (first result for "convolution mnist"). This is an example of a convolutional neural net for the MNIST data. We have (28, 28) grayscale image input and 60000 images. Num categories is 10.

This is the keras code he included. I've replaced comments with layer information, and dropped layers that have no effect on input/output/no parameters. Convolutions are deceptively simple, in that a convolution layer has only the number of parameters as the kernel size (plus a bias). Since this uses `padding='valid'`, this means for the given (3,3) kernel, the output is (x-2,y-2).

```
:::python
from keras import Sequential
from keras.layers import Conv2D, MaxPooling2D, Dropout, Flatten, Dense
model = Sequential()
# input = (28, 28, 1)

model.add(Conv2D(32, kernel_size=(3, 3),
                 activation='relu',
                 input_shape=(28, 28, 1)))

# output = (26, 26, 32)
# 32 conv layers * (9 kernel params + 1 bias param) = 320

model.add(Conv2D(64, (3, 3), activation='relu'))
# 32 channels
# output = (24, 24, 64)
# 64 conv * [(32 in channels * 9 kernel params) +  1 bias)] = 18496

model.add(MaxPooling2D(pool_size=(2, 2)))
# 0 param
# output = (12, 12, 64 )

model.add(Flatten())
# 0 param
# output = 9216

model.add(Dense(128, activation='relu'))
# params = (9216 + 1 bias)  * 128 = 1179776
# output = 128

model.add(Dense(10, activation='softmax'))
# params = (128 +1) * 10 = 1290
# output = 10

# also!
param_num = [lay.count_params() for lay in model.layers]
```

Now total parameters = 1,199,882. Yep, this simple-seeming model with 4 layers woth parameters has 1.2 million parameters. For a dataset that has 60,000 images, or 47 million pixels. It has a 99% classification accuracy. However, adding a 3rd convolution layer after the pooling step with 32 filters (`model.add(Conv2D(32, (3, 3), activation='relu'))`) would actually reduce the number of parameters to 448298. This is a bit counter-intuitive and is representative of how neural net structure needs to be looked at in more care than it's layer size.

In what other way could we develop a model with 1.2 million parameters (or even 450k). Any regression would have at most 28 x 28 = 784 inputs, any tree would be have parameters as number of leaves and boosting bagging would have ensemble size * average number of leaves. Taking mixture models, say K Gaussian mixtures would have 6K-1 parameters for a 2d space. Other than a neural net, I can't even think of another model that could use as many parameters (maybe SVMs, must investigate)

One of the reasons neural nets are so powerful is the sheer number of parameters we have it take, allowing for any kind of complexity to be modelled. The parametric forms of most stats try and keep this small to make it easier to calculate, but the nature of the structure means we have a much more complex structure than would otherwise be possible. And this is possible/feasible, primarily due to:

## The GPU

It's well known that training neural nets is embarrassingly parallel, and that GPUs are very good at parallel tasks. The result was obvious, but I don't think many people realise just how critical GPUs have been to the development of neural nets. At around 2012, clock cycles stopped improving like they were in the years before, Moore's law looked in danger of becoming the number of processors per chip and scientific programming community had been taking advantage of GPU and CUDA code to do various things to tap into more FLOPs than standard compute cores could provide.

As a GPU is a bunch of streaming multiprocessors ([See my talk on PyCUDA](https://github.com/nayyarv/PyCudaIntro) for more details), it's effectively a multicore cpu where number of cores are optimised over clock speed. Anything that could take advantage of many cores would gain huge benefits. And unlike CPU makers, GPU makers still had a lot of low hanging fruit left to grab, not to mention sticking additional cores wasn't a copout. While they would improve their micro-architecture every so often, the clock rates of each streaming processor hasn't improved greatly, but the number of them increases significantly. In fact, Intel sells versions of GPUs that are packed with CPU cores instead of GPU cores.

Without the aforementioned AlexNet leading the way, it'd be near impossible to conceive of the neural nets having the ubiquity they do. If you were limited to CPU only, I'd be very pessimisstic of seeing the benefits of neural nets we see today. Neural Nets aren't necessarily better on completely even playing field, but when is the field even? Comparing a neural net running on a GPU vs a neural net on a CPU is a pointless exercise in today's data science world. Given the sheer amount of computing power a neural net can harness in a way few other algorithms can, neural nets tend to be a magnitude more complex and correspondingly, a magnitude better. In today's world of large datasets, they're making use of it the best.

## The Data

The datasets in modern data science have shifted, and this is particularly evident in image data we have. Traditional stats would have a few thousand rows and tens to hundreds of predictors. Feature selection would happen a few ways (ridge, lasso, random forests) or maybe even dimensionality reduction (PCA, autoencoders), commonly augmented with some additional domain knowledge to help direct model building. And by and large, this is still the common paradigm for many data science tasks - select useful features and start building models.

But this job of feature selection fails in data that doesn't have such obvious structure. Images, text, video are examples of data that doesn't have a clear structure and despite the best efforts on NLP researchers, the success has been limited. And this is one of the areas deep learning really shines, it picks up it's own features quite well. If you're not sure about how to approach a problem, some deep learning can do most of it for you. 

However, the biggest drawback is the amount of data you need to train a neural net and this is why the feature select -> model process is still such a dominant paradigm, most datasets don't have the sheer amount of *labelled* data necessary to throw deep learning at the problem. While we're generating plenty of unlabelled data via things like  cursor tracking, image and video in social media, blog posts, reviews etc., these are rarely labelled and as such deep learning is of limited use. In fact, data collection can be one of the biggest expenses in running ML research and development. 

This is why unsupervised learning is still so popular, despite it's difficulty. Reinforcement learning has been a big beneficiary of deep learning since the algorithms generate and label their own data using reward functions and we can use neural nets to approximate the q tables when needed. Ideas such as GANs take inspiration from game theory to teach networks to generate images and ideas such as Variational Auto-encoders seek to find the latent variables of certain spaces, but these have had primarily niche uses so far. 


## We can be Data Scientists too!

All of this has led to Data Scientists of all kinds, from the bootcamps to the hardened mathematicians throwing neural nets at every problem that dares to rear it's head. We see CNNs and RNNs taking over the space. The packages such as tensorflow, pytorch etc. make it easy, the open data initiatives help a lot too, and the ease at which one can build a neural net has led to a near overspecialisation on Neural Nets. You can actually use neural net infrastructure to build logistic regressions, or even linear regressions should you choose to do so (though you don't get all the nice statistics on parameter usefulness and statistics on goodness of fit).

Does this mean you don't need Data Scientists? No, even just to build a neural net architecture you need a good understanding of parameter vs data space, you need to know how complex is the problem and thus how complex your architecture needs to be and you need to try a few different architectures. And to solve a problem, using a neural net is only 1 tool of many, it may not even be the appropriate tool for the problem. If you've got 100 predictors, 1000 observations, 10 outcoms, it's probably not be the right approach. Or if it needs to be delivered by a team that doesn't have a strong technical stack or if the neural net approach is only midly better, there are a lot of considerations that go into building data science solutions.

## The Future

Without Yann LeCunn's famous (but ultimately confusing with context) "Deep Learning is Dead", even Andrew Ng, deep learning's most famous champion, has stopped posting about it on twitter with such regularity. There's definitely a feeling that deep learning isn't giving us greater results as we throw new network architectures and computing power at the problem. It's growth is from it's application to various problems (from TB screening to automatically searching images). The more pessimistic are [saying we're in an AI winter](https://blog.piekniewski.info/2018/05/28/ai-winter-is-well-on-its-way/) (results have dried up and so too will funding), but what we're seeing is not the end of Deep Learning, rather the end of Deep Learning hype.

Problems with Deep Learning have become apparent, and primarily as people have become more well versed in it, they've also become more well-versed with it's limitations. The standard scientific approach of making big claims that get disproved in subsequent publications still holds even in Deep Learning and the twitter verse. The very hype driven nature of this field means that successes are shouted from all over while the embarrassing failures are hidden away (self driving car crashes aside). The fact that most of the research is being driven by large corporations (Baidu, Facebook etc) also represents a change in how machine learning has been advanced, and only exacerbated the hype machine without the pessimissim that academics level at anything daring to call itself 'new'.

Deep learning has definitely been revolutionary in the image/video space and will definitely stick around for a long time there (and likely other fields like language processing), until something new and well named comes along and displaces it. Nothing ever lives up to it's own hype after all, and frankly speaking, Deep Learning and Neural Nets haven't done too bad. For people in the field, neural nets are something we should know, but not to the exclusion of everything else, and it shouldn't be the only hammer in our toolkit (lest everything starts to look like a nail). As hype machines find new areas, we need to constantly throw away most of what we know and start again, likely multiple times throughout our career, and it's our foundations that allow us to approach new topics, pick up new things and work out how to apply new approaches to new problems, lest be become one trick pony.

## Aside: Bayesian Neural Nets

No discussion is complete without a Bayesian take on Neural Nets. That is a future topic and one I'm somewhat well versed in, having based my thesis in part on Radford Neal's Bayesian Neural Nets PhD. We're at the forefront of a resurgence in Bayesian Methods, which too deserves it's own post, but I'm going to leave a couple of papers to whet your appetites

1. Bayes By Backprop, or [Weight Uncertainty in Neural Networks](https://arxiv.org/pdf/1505.05424.pdf) - a very easy to follow paper that allows for distribution backprop to update the variational parameters of each weight with backprop-esque functions.
2. Radford Neal's PhD, [Bayesian Learning for Neural Networks](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.446.9306&rep=rep1&type=pdf) - Radford Neal is probably the professor I'd want to do a PhD under.  Among other things, he has developed his own branch of R, called pqR that is significantly better and I follow his blog to give myself a better understanding of language design fundamentals. This thesis (supervised by Geoff Hinton) is what I consider a foundational paper in this space, and while not perfect, is definitely incredibly influential. It's a little dense and uses a horrible font, but I think it's a very valuable resource to get a good understanding of Bayesian Neural Nets.
3. Packages like [pyro](http://pyro.ai/) and [edward](https://github.com/tensorflow/probability/blob/master/tensorflow_probability/python/edward2/README.md) are great places to start with deep probabilistic networks, though these are not the only choices in town.