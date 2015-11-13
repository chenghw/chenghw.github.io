---
layout: post
title: "JavaScript Toolbox"
date: 2015-11-12 16:51:50 -0500
comments: true
categories: "Flatiron&nbsp;School JavaScript"
---
Coming from Ruby to JavaScript was more difficult than I thought it would be. The main difference: Documentation. Ruby has <a href='https://ruby-doc.org/'>ruby-doc.org</a> which has an well written and well sorted dictionary for all their methods. While Javascript, I was primarily looking through <a href='http://www.w3schools.com/js/default.asp'>w3schools</a> and <a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference'>Modzilla's</a> documentation. Both not as well organized than Ruby's. Apart of my learning process is coming into a language knowing all my methods and functions. Nothing I found was to my liking so I decided to gather all the information on my own. What I came up with was surprisingly small. The JavaScript method library was tiny compared to Ruby. So I dived into each of the JavaScript functions that I thought I may use.

<table style="width:100%">
  <strong>Number</strong>
  <tr>
    <th align='center'>Function</th>
    <th align='center'>Description</th>
    <th align='center'>Example</th>
  </tr>
  <tr>
    <td>#toString()</td>
    <td>Returns a string of that number</td>
    <td>100.toString()<br>#=> "100"</td>
  </tr>
  <tr>
    <td>#toExponential(num=0)</td>
    <td>Returns the exponential of a float as a string, cannot be an integer (num option of how many decimal places)</td>
    <td>150.0.toExponential(4)<br>#=> "1.5000e+2"</td>
  </tr> 
  <tr>
    <td>#toFixed(num=0)</td>
    <td>Returns a string with the decimal places fixed to the num and rounds</td>
    <td>150.3261.toFixed(2)<br>#=> "150.33"</td>
  </tr> 
  <tr>
    <td>#toPrecision(num=length)</td>
    <td>Returns a string of the number with a fixed length from num</td><td>150.3261.toPrecision(2)<br>#=> "1.5e+2"</td>
  </tr> 
</table>

<table style="width:100%">
  <strong>String</strong>
  <tr>
    <th align='center'>Function</th>
    <th align='center'>Description</th>
    <th align='center'>Example</th>
  </tr>
  <tr>
    <td>#indexOf(string)</td>
    <td>Returns the index of the <strong>first</strong> occurence, returns -1 if none are found</td>
    <td>'hello'.indexOf('l');<br>#=> 2</td>
  </tr>
  <tr>
    <td>#indexLastOf(string)</td>
    <td>Returns the index of the <strong>last</strong> occurence, returns -1 if none are found</td>
    <td>'welcome'.indexLastOf('e');<br>#=> 6</td>
  </tr> 
  <tr>
    <td>#search(string)</td>
    <td>Same as <strong>#indexOf(string)</strong> except it allows for the search of regular expressions</td>
    <td>'t0'.search(/[0-9]/);<br>#=> 1</td>
  </tr> 
  <tr>
    <td>#match(string)</td>
    <td>Searches a string against a string or regular expression and returns the match in an array</td>
    <td>'mY'.match(/[A-Z]/);<br>#=> ["Y"]</td>
  </tr> 
  <tr>
    <td>#charAt(num)</td>
    <td>Returns the character at the num index and returned empty string if out of range</td>
    <td>'blog'.charAt(2);<br>#=> "o"</td>
  </tr>
  <tr>
    <td>#split('x')</td>
    <td>Splits string by 'x' into an array</td>
    <td>'string'.split('');<br>#=> ["s", "t", "r", "i", "n", "g"]</td>
  </tr>
  <tr>
    <td>#concat(*args)</td>
    <td>Takes in as many string arguments and combines them into one</td>
    <td>'java'.concat('scr', 'ipt');<br>#=> "javascript"</td>
  </tr>
  <tr>
    <td>#slice(num1, num2)</td>
    <td>Returns the sting from index num1 to num2 not including num2, can accept negative numbers</td>
    <td>'table'.slice(1,-1);<br>#=> "abl"</td>
  </tr>
  <tr>
    <td>#substring(num1, num2)</td>
    <td>Same as <strong>#slice(num1, num2)</strong> except it cannot accept negative numbers</td>
    <td>'enjoy'.substring(1, 3);<br>#=> "ej"</td>
  </tr>
  <tr>
    <td>#substr(num1, num2)</td>
    <td>Returns a string where the substring starts at index of num1 to num2 characters</td>
    <td>'yourself'.substr(1, 4);<br>#=> "ours"</td>
  </tr>
  <tr>
    <td>#replace(string1, string2)</td>
    <td>Finds and replaces the first instance of string1 with string2, then returns the resulting string</td>
    <td>'flatiron'.replace('iron', 'school');<br>#=> "flatschool"</td>
  </tr>
  <tr>
    <td>#toUpperCase()</td>
    <td>Upcase the entire string</td>
    <td>'flatiron'.upUpperCase();<br>#=> "FLATIRON"</td>
  </tr>
  <tr>
    <td>#toLowerCase()</td>
    <td>Lowercase the entire string</td>
    <td>'FLATIRON'.upUpperCase();<br>#=> "flatiron"</td>
  </tr>
  <tr>
    <td>#trim()</td>
    <td>Removes white space at the beginning and end of a string</td>
    <td>'  flatiron?  '.trim()<br>#=> "flatiron?"</td>
  </tr>
</table>

<table style="width:100%">
  <strong>Array</strong>
  <tr>
    <th align='center'>Function</th>
    <th align='center'>Description</th>
    <th align='center'>Example</th>
  </tr>
  <tr>
    <td>#toString()</td>
    <td>Returns a string of that number</td>
    <td>100.toString()<br>#=> "100"</td>
  </tr>
  <tr>
    <td>#toExponential(num=0)</td>
    <td>Returns the exponential of a float as a string, cannot be an integer (num option of how many decimal places)</td>
    <td>150.0.toExponential(4)<br>#=> "1.5000e+2"</td>
  </tr> 
  <tr>
    <td>#toFixed(num=0)</td>
    <td>Returns a string with the decimal places fixed to the num and rounds</td>
    <td>150.3261.toFixed(2)<br>#=> "150.33"</td>
  </tr> 
  <tr>
    <td>#toPrecision(num=length)</td>
    <td>Returns a string of the number with a fixed length from num</td><td>150.3261.toPrecision(2)<br>#=> "1.5e+2"</td>
  </tr> 
</table>
