---
layout: post
title: "ScalaFunctional: Get the Power of Functional Programing From Scala and Apache Spark...in Python"
modified:
categories: Data-Science 
excerpt:
comments: true
tags: [python, data wrangling]
image:
  feature:
date: 2015-09-14T16:32:34+08:00
use_toc: true
---

For me, as a Apache Spark and Scala-as-the-first-functional-programming-language user, it is totally torture when I have to wrangle data in Python even with Pandas. The functional programming mechanisms provided by native python implementation were't that comprehensive and handy. 

So I had always wanted to implement something like [Resilient Distributed Dataset](http://spark.apache.org/docs/latest/programming-guide.html) let developers easily to map, reduce, group data and so on with the beautiful things already happening in Scala or Spark. 

Fortunately, [Pedro Rodriguez](https://github.com/EntilZha), the author of [**ScalaFunctional**](https://github.com/EntilZha/ScalaFunctional), has done a great work, which allows us to manipulate the data like charm as Scala does!

# ScalaFunctional

> **ScalaFunctional** exists to make functional programming with collections easy and intuitive in Python. It borrows the functional programming APIs from Scala and Apache Spark.

[**ScalaFunctional**](https://github.com/EntilZha/ScalaFunctional) is a Python library allowing you to wrangle data around like what you did in the old time in Scala and Apache Spark. It is more intuitive to write, and your code can be more readible.

[ScalaFunctional's document](http://scalafunctional.readthedocs.org/en/latest/)

## How to install

The installation is easy peasy. Just follow one of the two following methods. 

```sh
pip install scalafunctional
```

or

```sh
git clone https://github.com/EntilZha/ScalaFunctional.git
cd ScalaFunctional.git
python setup.py develop
```
---

# Pain in The Ass

Of course Python comes with a bunch of functional programming mechanism like `map`, `reduce`, `filter` and `xrange`, but the implementation is quite unhandy. Instead of allowing for functional operations to be chained one after another, Python forces embedded calls which rapidly become difficult to read and write. The following are examples how Scala and Python doing Number Twiddling. (examples from [doc of ScalaFunctional](http://pedrorodriguez.io/blog/2015/03/14/functional-programming-collections-python/))

## Python
```python
numbers = [-3, -2, -1, 1, 2, 3]

map(lambda x: x * 2, numbers) 
# [-6, -4, -2, 2, 4, 6]
filter(lambda x: x > 0, numbers) 
# [1, 2, 3]

reduce(lambda x, y: x + y, map(lambda x: x * 2, filter(lambda x: x > 0, numbers))) 
# 12

# Factorials from 9 and down
map(lambda l: reduce(lambda x, y: x * y, l), [range(1, i) for i in range(2,11)])
# [1, 2, 6, 24, 120, 720, 5040, 40320, 362880]
```

## Scala
```scala
val numbers = List(-3, -2, -1, 1, 2, 3)
scala> numbers.map(x => x * 2)
res0: List[Int] = List(-6, -4, -2, 2, 4, 6)

// Filter out negative values
scala> numbers.filter(x => x > 0)
res1: List[Int] = List(1, 2, 3)

// Get the sum of double each positive element
scala> numbers.filter(x => x > 0).map(x => x * 2).reduce((x, y) => x + y)
res2: Int = 12

// Calculate the factorials from 9 down
scala> val range = List(1, 2, 3, 4, 5, 6, 7, 8, 9)
scala> range.inits.map(l => l.product).toList
res9: List[Int] = List(362880, 40320, 5040, 720, 120, 24, 6, 2, 1, 1)
```

As you can see, in Python, even the simpliest functional operations can be very messy. [Method chaining](https://en.wikipedia.org/wiki/Method_chaining) like what we did in Scala comes to rescue.

As the method chaining can maximize the readibility of functional operations, and for developers, it makes our code much easier to be writen. 

> The best part, is that **each operation sequentially describes how the data is transformed**.

So with ScalaFunctional, we can rewrite the some Python code like this:

## ScalaFunctional
```python
from functional import seq
numbers = seq([-3, -2, -1, 1, 2, 3])

numbers.map(lambda x: x * 2)
# [-6, -4, -2, 2, 4, 6]
numbers.filter(lambda x: x > 0)
# [1, 2, 3]

numbers.filter(lambda x: x > 0).map(lambda x: x * 2).reduce(lambda x, y: x + y)
# 12

# Factorials from 9 and down
numbers = seq([1, 2, 3, 4, 5, 6, 7, 8, 9])
numbers.inits.map(lambda x: x.products())
# [1, 2, 6, 24, 120, 720, 5040, 40320, 362880]
```

Nice and beautiful, isn't it! ScalaFunctional brings the beauty to Python! Why not try it out right now?

If there is Actor function or multiprocess mechanism would be totally killer for me.

# Reference

1. [A practical introduction to functional programming](http://maryrosecook.com/blog/post/a-practical-introduction-to-functional-programming)

2. [Resilient Distributed Dataset](http://spark.apache.org/docs/latest/programming-guide.html)

3. [ScalaFunctional](https://github.com/EntilZha/ScalaFunctional)




