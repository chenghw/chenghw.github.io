---
layout: post
title: "Binary Search Tree in Ruby"
date: 2015-12-21 15:01:14 -0500
comments: true
categories: "Flatiron&nbsp;School binary&nbsp;search&nbsp;tree Ruby"
---

I am officially a Flatiron School graduate!! 12 weeks of learning Ruby, Object Oriented Programming, Test Driven Development, RSpec, Model View Controller, REST, CRUD, rack middleware, Sinatra, Ruby on Rails, Active Record, SQL, JavaScript, jQuery, AJAX, Handlebars and Ember.js. But most importantly coming out with the knowledge of how to approach and learn a new language. I look forward to my life after Flatiron and what new languages and frameworks I'll learn.

I wanted to touch upon a topic we started covering in our last week at Flatiron, which were data structures and sorting algorithms. This week reminded me of my few years of taking computer science courses, creating our own stacks, queues and linked lists. Writing sorting algorithms such as quicksort, mergesort and bubble sort. I was ecstatic to find out we were covering these topics! Remembering how much fun I had with these is partially what got me to change careers and enroll in Flatiron School in the first place. Even back in week 1 I was asking myself, what kind of sort does Ruby use? I learned so many sorts long ago, which one is it? After some Google-ing, interestingly enough, Ruby uses the quicksort algorithm for its sort method over mergesort.

<h1>Binary Search Tree</h1>
So one of my favorite problems that I came across was constructing your own Binary Search Tree(BST). I am going to walk through my process, but first we need to know what a BST is. A BST is a series of connecting nodes, where each node contains data, a left and a right. The left and right are pointers to a subtree of nodes where left is less than or equal to and right is greater than.

With this information we can start by creating our Binary Search Tree class which will represent our data structure. The walkthrough will consist of the structure and inserting into the BST.

``` ruby
class BST

end
```
<br>
Back to what a BST contains: data, left and right. Data will represent the data we store and left and right will represent subtrees.

``` ruby
class BST
  attr_accessor :data, :left, :right

  def initialize(data)
    @data = data
  end
end
```
<br>
Great! Now that we have the basic structure of the BST, we will need to be able to insert data into our BST class. Lets create a insert method which takes in 1 argument, data. I'm going to go ahead and pseudocode my thought process of how I think it works.
``` ruby
  def insert(data)
    # 1 - Start at top of the tree
    # 2 - Find which direction insert should be
    # 3 - Check that direction if it is nil
    # 3a - If nil insert into that location
    # 3b - If not nil, change top of tree location to that node
    # 4 - Repeat step 1
  end
```
<br>
We start at the top of the tree and keep track of the location. Following this, compare the data being inserted into our tree with the current location. This will determine if we are going left or right. If that direction results in a nil, we have reached our destination! We insert here, but if not we will need to change the current location to the top of the subtree.
``` ruby
  def insert(data)
    # 1 - Start at top of the tree √
    # 2 - Find which direction insert should be √
    # 3 - Check that direction if it is nil √
    # 3a - If nil insert into that location √
    # 3b - If not nil, change top of tree location to that node √
    # 4 - Repeat step 1

    current_location = self
    if current_location.data >= data
      if current_location.left
        current_location = current_location.left
      else
        current_location.left = BST.new(data)
      end
    else
      if current_location.right
        current_location = current_location.right
      else
        current_location.right = BST.new(data)
      end
    end
  end
```
<br>
We want to keep doing this process until the data has been inserted into the correct location. Since the number of times this loop will run is unknown, a while or until loop will do the trick with a placeholder variable for confirmation of when the loop is finished.
``` ruby
  def insert(data)
    current_location = self
    inserted = false

    until inserted
      if current_location.data >= data
        if current_location.left
          current_location = current_location.left
        else
          current_location.left = BST.new(data)
          inserted = true
        end
      else
        if current_location.right
          current_location = current_location.right
        else
          current_location.right = BST.new(data)
          inserted = true
        end
      end
    end
  end
```
<br>
Running some tests that were developed prior and eureka!! It works! While our task is complete, I'm not satisfied. To me this looks dirty. The 2 variables declared outside the loop, the loop itself, the seemingly repetitive code inside the loop and all the if-else statements!! I needed to refractor this. So back to thinking about the 5 steps, it appears the first 4 steps are repeated on BST instances, where each time all that is changing is the BST is becoming a subtree of itself. It seems like this can be done recursively.
``` ruby
  def insert(data)
    # 1 - Find which direction insert should be
    # 2a - If nil insert into that location
    # 2b - Else call insert method again on that subtree
  end
```
<br>
With recursion I am able to clean up the code to something I am satisfied with.
``` ruby
  def insert(data)
    # 1 - Find which direction insert should be √
    # 2a - If nil insert into that location √
    # 2b - Else call insert method again on that subtree √

    if self.data >= data
      self.left == nil ? self.left = BST.new(data) : self.left.insert(data)
    else
      self.right == nil ? self.right = BST.new(data) : self.right.insert(data)
    end
  end
```
<br>
This was just the first step in creating the BST data structure. Next I'll explore deletion, searching and sorting in Binary Search Trees.
