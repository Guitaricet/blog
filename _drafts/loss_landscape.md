# What Deep Learning Theories Can Tell Us Today

Deep learning has been with us for a while and mostly it’s been studied in a very practice-first way.
And it had its pros, a lot of them.
Deep learning changed how people communicate using different languages by greatly improving machine translation quality.
It is an essential part of modern dialogue systems such as Siri, Alexa, and Google Assistant.
And you can do a bunch of cool stuff with photos and videos including deoldifying, enhancing the quality and so on.

But if we are talking science here, there are many reasons to deviate from such an approach and to try to
understand why our practical results are so good.
Because classic ML and basic reasoning tell us that neural networks should not be useful at all.

In this small series of posts we will talk about the state of modern deep learning theories that try to explain deep learning
success and to get some new insights about it.
We will mostly discuss the results omiting the proofs and precice theorem formulations and proofs.
This series is written by practice people who are interested in what is happening in theory and 
we would not claim that it reviews most of the key theoretical works that shape our new vision of deep learning,
but we like to mention some of the results we personally find interesting and important.

We want to start with the question of why we are able to optimize neural networks using simple gradient descent methods
and not to be stuck in some bad local minimum.

## How bad is this local minimum?

Let’s look at a picture you probably saw in your university classes.
It is about gradient descent and convex optimization.

![gradient descent]()

Gradient descent is greedy.
It just improves your loss locally and it is commonly accepted that GS is guaranteed to converge to a global minimum only
in a convex setup.
On the other hand, the neural network loss landscape is highly complex and nonconvex.

From the math side it looks like this:

<dirivation>

And from the empirical side it looks like this:

<picture from the Microsoft paper on analyzing loss landscape>

but also like this:

<picture of loss reaching zero or accuracy reaching 1>

Several researchers who did neural networks before the era of deep learning, including Yann LeCun, say that the fact that NNs can be optimized using gradient descent fascinates them and people would not expect it to work back in the days.

But it does. And why is not the question of applied DL, but is the question of theory. Take linear (or logistic) regression which is the simplest kind of neural network one can find. Linear regression loss is just (y - Ax)^2 which is simple and convex and only has one local minimum - its global minimum.

<picture of parabola>

Lu and Kawaguchi (2017) studied a bit more complex form of a neural network. Linear neural network - one that does not have nonlinear activation functions - A_N A_N-1 … A_1 x. It is easy to see that such a network, just like linear regression, can only describe linear functions. But the optimization problem is not trivial and the loss-landscape is not convex. Their result is quite fascinating. These networks have multiple local minima, but they are all the same. So even if you always go the steepest curve you find the lowest valley!

<probably, a picture of multiple valleys of the same minimum value>

