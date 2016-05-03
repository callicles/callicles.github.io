---
published: true
layout: post
date: 2016-05-03T09:51:00.000Z
categories: "Computer-Science"
---
The Internet is a network of computers: a web of machines connected with one another in a seemingly random pattern.

<img src="{{site.baseurl}}/assets/images/clos/network.png" alt="Network" style="max-width: 500px; margin: 0 auto;" />

But when you dive into the nitty gritty details of how the network is actually structured. It is structured in a very interesting way. Instead of being connected directly to one another like the previous drawing suggested, they are linked together through an intermediate piece of hardware either called a router or a switch. let’s draw a parallel to the old days of the telephone. The internet works similarly to the phone operator, you’d make a request and the operator would connect you with someone else.

![Operator and switch]({{site.baseurl}}/assets/images/operator.png)

This is the piece of the puzzle we are going to look at: the switch. The switch is the wiring that connects everything together.


## Cross Bar Networks

Cross bars are one of the basic ways to connect 2 arrays of devices to each other so that each input has access to all of the outputs. Think of it like a road grid. You need to connect 2 towns to 2 other towns with highways. How would you do it ?

![cross bar]({{site.baseurl}}/assets/images/grid.png)

The previous image underlines the analogy between city connections and the cross bar network. The cities on the left are connected with highways on the left. On the right, in the electronic system, inputs and outputs are connected with wires. Continuing with the highway analogy - The parts highlighted in red on the left are interchanges on the highway. On the right, for the electronic topology, these red points are switches.

One of the issues with that type of network topology is that building the network with all the switches and connections gets really expensive when the number inputs and outputs get really big.

This is when Clos network comes to the rescue.


## Clos Networks

Clos networks are networks whose topology are based on cross bar networks. Let's consider our switchboard phone operator from before as a crossbar network. They have calls coming in and have to connect the incoming call to the line the customer wants to reach.

![OneOperator]({{site.baseurl}}/assets/images/OneOperator.png)

Now, if a lot of calls come in, the operator will be completely overwhelmed and will not be able to connect all the calls. The idea here is that we are going to multiply the number of operators to answer the demand.

![Multiplying operators]({{site.baseurl}}/assets/images/TwoOperators2.png)

The result of the previous design is that now incoming lines and outgoing lines are linked with a particular operator. So that if you want to connect with someone who's line is on another operator's board, you can't.

To fix that design flaw we will add one layer of operators.

![2 layers]({{site.baseurl}}/assets/images/2Layersxcf.png)

Now that we have 2 layers of operators everybody can contact anybody in the network. However, there is still one big downside to the system. 2 people linked to the same ingress operator can't talk at the same time with other people on the same egress operator. There is only one line available between an ingress operator and an egress operator !

Fortunately though, adding another layer of operators will also solve that problem.

<img src="{{site.baseurl}}/assets/images/ClosNetwork.png" alt="ClosNetwork" style="max-width: 800px; margin: 0 auto;" />

Now, each ingress is connected exactly once to all the middle operators. All the middle operators are connected to all the ingress and egress operators. And, finally, all the egress operators are connected to all the middle operators. Now there are different paths to get from one ingress operator to an egress operator. Actually the number of paths is exactly the number of operators in the middle layer.

That type of network has some interesting properties when you play with the number of operators in the middle and the number of layers. Considering m the number of operators in the middle layer and n the number of lines to be connected together, if m ≥ 2n−1 the network will be strictly non blocking. This means that an incoming call can always be connected to an unused line without having to rearrange ongoing calls on the network. If the verified property is m ≥ n, then every incoming call can be connected to a free line but we may have to rearrange existing connections in the network to connect people through.

Finally, another interesting consideration is that for big enough network, it is cheaper to build a Clos network than a Cross bar networks, even if the Clos network is built from cross bar networks.

### Reference:

* [Clos Network - Wikipedia](https://en.wikipedia.org/wiki/Clos_network)
