## Exploring the famous twin spirals problem (Lang and Witbrock 1988)

### Introduction

The earliest neural networks (Rosenblatt's perceptrons) could only act as linear classifiers, as famously shown by Minsky and Papert. Linear classifier means that they could only separate data points by a straight line, plane, or hyperplane (depending on the number of dimensions). Neural networks with hidden layers could draw more complicated decision boundaries, and solved the famous XOR problem that had been originally posed by Minsky & Papert.
However even then, early neural networks, with simple densely connected linear models, were unable to classify apart data points that lay along two interleaved spirals, as depicted in the image below (looks a bit like a spiral galaxy).
![twin_spirals](https://i.ibb.co/1R4xr79/Twin-spirals.jpg)

This program displays two different approaches to classify the spirals. Most importantly, it shows the value of transforming the problem space. By transforming the domain from rectangular to polar coordinates, we get a more elegant objective function, and are able to calculate it faster. We also see that even without domain transformation, a complex-enough network can solve the problem to an arbitrary degree of accuracy, even if the resulting classification (and objective function) might not be elegant to the human eye. 

### Examples

#### Cartesian
Without transformation to polar space, we use progressively larger/deeper linear neural nets to classify  the points. We get unsmooth and outlandish objective functions partitioning the problem space, but they do to the job:

This net has 10 hidden nodes, and sets initial weights to the value 0.5. Classification accuracy is around 93%.

![10_hidden_nodes](https://i.ibb.co/hsmWjs5/02-raw-out-10nodes-init-0-5-swinging-around-93.png)

This one has accuracy 98%:

![10_nodes_2](https://i.ibb.co/LkwP2JN/01-raw-out-10nodes-98pc.png)

While this one has practically 100% accuracy:

![14_nodes](https://i.ibb.co/RjXKV7s/08-14-nodes-defaults-3900-eps-raw-out.png)

(the code for these nets is given in the files)

#### Polar

Now we repeat the above problem but during preprocessing, convert the Cartesian-system coordinates to polar coordinates. 

This one gives a much more elegant looking objective function, and 77% accuracy.

![77_accuracy](https://i.ibb.co/8jc3pMC/polar-out-6nodes-77-8acc-after20k-epochs.png)

This one, with 7 hidden nodes, has perfect accuracy and converges pretty fast.

![7_hidden_nodes](https://i.ibb.co/c2StVst/polar-out-7nodes-converged5900.png)

And finally this one has 16 hidden nodes.

![16_nodes](https://i.ibb.co/0FTnTzp/polar-out-16nodes-3200ep.png)

We can see that conversion to polar coordinates transforms the problem effectively into one of linear separation (though when displayed to us after reconversion, the decision surface looks circular or spiral).



