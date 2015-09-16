---
layout: post
title:  "Scala School september 2015 Meetups"
date:   2015-09-15 18:42:00
categories: Meetups
---

Today I was at the at the New York scala school, we had some fun time implementing linked list methods. The idea was to give some introductions to some of the scala concepts.

The slides of the presentation are available [here](http://mattbanister.github.io/scala-nyc-uni).

What I mainly got out of this presentation is the existence of sealed traits which are traits that cannot be extended outside of the file. As a result the compiler is able to get all the subtypes and give you a lot of insights at compilation time.

From the presentation was given this example:

{% highlight Scala %}
sealed trait Answer

case object Yes extends Answer
case object No extends Answer

val x: Answer = Yes
x match {
  case No => println("No")
}
{% endhighlight %}

Will give the compiler warning:

~~~
<console>:14: warning: match may not be exhaustive.
It would fail on the following input: Yes
              x match {
              ^
scala.MatchError: Yes (of class Yes$)
~~~

Finally, we implemented some linked list methods. Here is the skeleton of the project.

{% highlight Scala %}
case object MNil extends MList
case class MCons(head: Int, tail: MList) extends MList

sealed trait MList {
  def length: Int = this match {
    case MNil => 0
    case MCons(h, t) => 1 + t.length
  }
  def sum: Int = ???
  def map(f: Int => Int): MList = ???
  def filter(f: Int => Boolean): MList = ???
  def append(e: Int): MList = ???
  def reverse: MList = ???
}


val myList: MList = MCons(1, MCons(2, MCons(3, MCons(4, MNil))))
myList.length //4


// Provide implementations for the following methods...
myList.sum // res1: Int = 10
myList.map(_ + 1) // res2: MList = MCons(2,MCons(3,MCons(4,MCons(5,MNil))))
myList.filter(_ % 2 == 0) // res3: MList = MCons(1,MCons(3,MNil))
myList.append(5) // MCons(1,MCons(2,MCons(3,MCons(4,MCons(5,MNil)))))
myList.reverse // MCons(4,MCons(3,MCons(2,MCons(1,MNil))))
{% endhighlight %}
