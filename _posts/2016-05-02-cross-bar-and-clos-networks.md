---
published: true
layout: post
date: 2016-05-02T17:36:00.000Z
categories: "Computer-Science"
---
Internet is a network of computers, a web of machines connected with one another in a seemingly chaosive pattern.

<img src="{{site.baseurl}}/assets/images/clos/network.png" alt="Network" style="max-width: 500px; margin: 0 auto;" />

But when you zoom in and get into the nitty gritty details the network is actually structured in a very interesting way. Instead of being connected directly to one another like the previous drawing suggested, they are linked together through an intermediate piece of hardware either called a routeur or a switch. If you want to draw a paralell with the old days of the telephone, you can compare the switch to the operator you would get on the phone when you would ask him to connect you with someone else.

![Operator and switch]({{site.baseurl}}/assets/images/operator.png)

This is the piece of the puzzle we are going to look at. The switch. How is the wiring made to connect everything together.


## Cross Bar Networks

Cross bars is the most basic way to connect 2 arrays of devices with each other so that each input has access to all the ouputs. Think of it like a road grid. You need to connect 2 towns to two other towns with highways. How would you do it ?

![cross bar]({{site.baseurl}}/assets/images/grid.png)


The previous image underlines the analogy between city connections and the cross bar network. The cities on the left are connected with highways on the left. On the right, in the electronic system, inputs and outputs are connected with wires. The part highlighted in red are the interchange on the highway analogy and switches on the electronic side.

One of the issues with that type of network topology is that building the network with all the switches and connections gets really expensive when the number inputs and outputs get really big.

This is when clos network comes to the rescue.


## Clos Networks

Clos networks are networks whose topology are based on cross bar networks. Let's consider our switchboard operator from before as a crossbar network. They have calls coming in and have to connect the incoming call to the line the customer wants to reach.

![OneOperator]({{site.baseurl}}/assets/images/OneOperator.png)

Now If a lot of calls come in, the operator will be completely overwhelmed and will not be able to patch through all the calls. The intuition here is that we are going to multiply the number of operators to answer the demand.

![Multiplying operators]({{site.baseurl}}/assets/images/TwoOperators2.png)

The result of the previous design is that now incoming lines and outgoing lines are linked with a particular operator. So that if you want to connect with someone who's line is on another operator's board, you can't.

To fix that design flaw we will add one layer of operators.

![2 layers]({{site.baseurl}}/assets/images/2Layersxcf.png)

Now that we have two layers of operators everybody can contact everybody in the network. However, there is still one big downsize to the system. Two people linked to the same ingress operator can't talk at the same time with other people on the same egress operator. There is only one line available between an ingress operator and an egress operator !

Fortunatly adding another layer of operators will also solve that problem.

<img src="{{site.baseurl}}/assets/images/ClosNetwork.png" alt="ClosNetwork" style="max-width: 800px; margin: 0 auto;" />

Now, each ingress is connected exactly once to all the middle operators. All the middle operators are connected to all the ingress and egress operators. And finaly all the egress operators are connected to all the middle operators. Now that way there are different paths to get from one ingress operator to an egress operator. Actually the number of paths is exactly the number of operators in the middle layer.

That type of network has some interesting properties when you ply with the number of operators in the middle and the number of layers. Considering m the number of operators in the middle layer and n the number of lines to be connected together then if m ≥ 2n−1 the network will be strictly non blocking. Meaning that an incoming call can always be connected to an unsed line without having to rearange ongoing calls on the network. If the verified property is m ≥ n, then every incoming call will be able to be connected to a free line but we may have to rearange exsisting connections in the network to patch people through.

Finaly another interesting consideration is that for big enough network, it is cheaper to build a clos network than a Cross bar network, even if the clos network is built from cross bar networks.

### Reference:

* [Clos Network - Wikipedia](https://en.wikipedia.org/wiki/Clos_network)
