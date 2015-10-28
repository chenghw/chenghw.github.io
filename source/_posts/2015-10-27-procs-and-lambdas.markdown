---
layout: post
title: "Procs and Lambdas"
date: 2015-10-27 09:15:10 -0400
comments: true
categories: "Flatiron&nbsp;School block proc lambda"
---

<p>I am a big believer in fundamentals and foundation. In grade school I was horrific in Spanish. Being close to failing and having to repeat the previous years Spanish class, my parents sent me to summer school. I learned the fundamentals of the language and went into the following year understanding concepts which I didn't have the tools to comprehend previously.</p>

<p>We were told a quote early on in the semester which has stuck with me. It was along the lines of, "The problem isn't with Rails, but with your Ruby." I took away to truly understand Rails was to truly understand the fundaments and the foundation that Rails was built on.</p>

<p>Before diving into Proc and Lambdas which I saw as one of those fundamentals/building blocks of the Ruby language, we must go over what a Block is first.</p>

<h2>Blocks</h2>
<p>A block is a block of code or a code block, thus the name <strong>block</strong>. A list of instructions for your code to follow. Blocks can be identified by do...end or { }. There is a saying in Ruby land that everything in Ruby is an object, however that does not apply here. A block is not an object! Which brings us to procs and lambdas.</p>

<h2>Procs</h2>
<p>Proc, stands for <strong>proc</strong>edure, is a block of code which is an object. This means procs can be passed through in method arguments, be something a method returns and have methods called upon them.</p>
``` ruby Creating a proc
square = Proc.new{ |x| x**2 }

square = Proc.new do |x|
  x**2
end
```
<p>Up until now we mostly been using blocks in enumerables. Procs can take the place of blocks in enumerables.</p>
``` ruby Using a proc in an enumerable
[ 1, 2, 3, 5, 7 ].map(&square)
 => [1, 4, 9, 25, 49] 
```
But lets say you don't want to just pass in 1 value. Using an iterator now seems to not be the right tool for the job. There is the call method.
``` ruby Call method
[ 15 ].map(&square)
 => [225]
 
 square.call( 15 )
 => 225 
```
<p>Another benefit procs over blocks is that they can be returned.</p>
``` ruby Proc as a return
class Player
  attr_accessor :coins
  def initialize
    @coins = 1000
  end
end

class Team
  attr_accessor :status
  def result
    if status
      Proc.new{ |p| p.coins += 150 }
    else
      Proc.new{ |p| p.coins -= 100 }
    end
  end
end

player1 = Player.new
player2 = Player.new
team = Team.new
team.status = true
proc = team.result

[ player1, player2 ].each(&proc)
=> [#<Player:0x007f9682936fa0 @coins=1150>, #<Player:0x007f968204d1a0 @coins=1150>]

player1.coins
=> 1150
```
<h2>Lambda</h2>
<p>A lambda is also a block of code which is an object. This is because a lambda is apart of the Proc class.</p>
``` ruby Creating a lambda
woofs = lambda{ |x| "Woof!"*x }

woofs = lambda do |x|
  "Woof!"*x
end

=> <Proc:0x007f9683183dc0@(irb):152 (lambda)> 
```
<h2>Procs vs Lambdas</h2>
<p>1 - Procs and lambdas treat arguments differently. Procs do not check for the correct number or arguments while lambdas do.</p>
``` ruby Argument validation
hello = Proc.new{ |name| "Hello #{name}!" }
goodbye = lambda{ |name| "Good-bye #{name}!" }
hello.call
=> "Hello !"
goodbye.call
=> ArgumentError: wrong number of arguments (0 for 1)
```
<p>2 - Proc and lambdas treat returns differently. A return inside a proc will be treated as a return for the entire method which it is inside, while a return inside a lambda will only be treated as the return for inside the lambda.</p>
``` ruby Returns
def proc_return
  proc = Proc.new do
    return "Hi from inside the proc!"
    puts "Do you see me?"
  end
  puts proc.call
  puts "Does this even show up?"
end

proc_return
 => "Hi from inside the proc!" 

def lambda_return
  lambda = lambda do
    return "Hi from inside the lambda"
    puts "Do you see me?"
  end
  puts lambda.call
  puts "Does this even show up?"
end

lambda_return
Hi from inside the lambda
Does this even show up?
 => nil 
```

<h2> & </h2>
``` ruby & Clarification
[ 'a', 'b', 'c' ].map( &:upcase )
[ 'a', 'b', 'c' ].map{ |letter| letter.send( sym ) }
=> ["A", "B", "C"] 
```

<h2> Additional Examples </h2>
``` ruby Examples
animal_sounds = {
  'cat' => lambda{ |x| "Meow"*x},
  'dog' => lambda{ |x| "Woof"*x},
  'pig' => lambda{ |x| "Oink"*x},
  'bird' => lambda{ |x| "Kakaw"*x}
}
animal_sounds['bird'].call(2)
=> "KakawKakaw" 
```