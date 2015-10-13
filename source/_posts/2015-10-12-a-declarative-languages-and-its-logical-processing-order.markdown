---
layout: post
title: "A Declarative Languages and Its Logical Processing Order"
date: 2015-10-12 23:02:42 -0400
comments: true
categories: "Flatiron&nbsp;School SQL"
---

After two intense weeks at Flatiron School learning Ruby, we've moved onto SQL, a totally different langauge. Where Ruby is an object oriented programming language used in web development, SQL is a declarative language designed to manage and query databases.

The transition for me was very tough going from Ruby to SQL. Ruby being a very literal language where it reacts to everything I type typically the way I would expect. Not to say I don't run into errors, but with tools like Pry and RSpec, debugging is managable. While this do that. For each element do this. The Ruby flow control made sense.

Now for SQL, I read it like any other language I encountered, from beginning to end, top to bottom. It made sense in the beginning, but started to not make sense when I got introduced to aggregate functions. Using a 'COUNT' with a 'WHERE' created errors which is where I learned to implement 'HAVING'. Essentially serving the same purpose as 'WHERE' for the query I was making, but one was necessary for aggregate functions. This sparked my curiosity and I asked myself, do I really know what is happening here?

My answer. No. I didn't really know what was happening behind the scenes and how my queries were being compiled. So I posed the question. If reading the query from beginning to end is not correct, then there must be some sort of order of opperation that SQL follows in reading syntax. But the answer I found was very unsatisfying. SQL is not like any language that I have encountered. SQL is a declarative language. Declarative language syntax is describing what the program should return rather than how this task should be accomplished. In simple terms, you tell SQL what you want and SQL will find a way to get it for you on through its own methods.

But there must be still rules like how I have to use 'HAVING' instead of 'WHILE'!! Well, there is something that we can use in fact, for 'SELECT' statements at least. 'Logical Processing Order' determines the order of which objects are defined and made available to other sections of the 'SELECT' statement.

<ol><strong>Logical Processing Order</strong>
<li>FROM</li>
<li>ON</li>
<li>JOIN</li>
<li>WHERE</li>
<li>GROUP BY</li>
<li>WITH CUBE or WITH ROLLUP</li>
<li>HAVING</li>
<li>SELECT</li>
<li>DISTINCT</li>
<li>ORDER BY</li>
<li>TOP (LIMIT)</li>
</ol>

Using the 'Logical Processing Order' for 'SELECT' statements, I was able to break down the task of creating 'SELECT' statements into more managable steps.

Step #1 - Processes 1-3, what tables will I need to join for me to have all the information I need.

Step #2 - Processes 4-7, are there aggregate functions I need to account? If so, then I know I will need a 'GROUP BY', and if there is conditional logic to account for then I will need to use 'HAVING' instead of 'WHERE'.

Step #3 - Process 8, what variables do I want in my 'SELECT' statement and do I want to rename any with 'AS'?

Step #4 - Processes 9-11, am I looking for the query to output in a specific order or by a limit?

Knowing the control flow and asking the right questions.