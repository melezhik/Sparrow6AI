# Examples for sparrow.ai bot

# Q1 Hello word

Question:

I have a text with "hello world" string, please create task.check to verify
the text contains the string

Answer:

```
hello world
```

Explanation:

Task check dsl uses so called plain checks to verify some data contains some strings.
It parses text in line by line mode and looks for strings specified in task.check
Plain checks are just normal plain strings. We can have as many plain checks as we need
in task check code, for example:

```
hello
world
```

Would check that text contains both `hello` and `world` strings

# Q2 Regular expressions

Question:

I have a text with "hello world" string, please create task.check to verify
the text contains the string, case insensitive

Answer:

```
regexp: :i "hello world"
```

Explanation:

Task check dsl uses so called regular expression checks to verify some data contains some strings
matching Regular expressions. In this example we use so called regular expression modifier
(:i) to enable case insensitive matching. Raku regular expression should be placed
after reserved `regxp: ` prefix.

# Q3 Sequential checks 

Question:

I have a text with numbers 1,2,4,5 going back to back ,
so that every number takes exactly one line:

1
2
3
4
5

Please create task.check to verify
the text contains those number going back to back sequentially 

Answer:

```
begin:
1
2
3
4
5
end:
```

Explanation:

we use so called sequential mode by using reserved 
begin: and end: expressions . All the checks inside begin:/end: block are executed in sequential mode , we insist that numbers inside block ( if any of them found ) should go strictly back to back , so in other words the numbers order is important. 

begin: and end: expression sets a scope for sequential search mode. Only check expressions inside the block are applied in sequential mode. You can use and checks  - plain checks or regular expressions inside the block, in our example we use plan checks to check that lines contain required numbers. To start sequential mode use  begin: expression, to end the mode use end: expression. Make it sure you always close sequential mode with end: expression or you end up applying it for the rest of check rules in task check code 

# Q4 Search text within block of lines or range mode

Question:

I have following text:

```
start
line1
line2
line3
stop
```

i would like to verify that line1, line2, line3
are between line containg word start and line 
containing word stop

Answer:

```
between: { start } { stop }
regexp: ^^ line \d+ $$
end:
```

Explanation:

To verify that some lines are inside some block of text you should use so called range expressions also known as range or within blocks. Range expression has start and end subexpression. Subexpression defines start and end line of a block and should contain Raku regular expression inside curly brackets.
Line in the begining of the block and in the end of the block should match corresponding
Raku regular expressions. 

Rules aka check exoressions inside range block 
are applied to all the lines that happen to be 
inside the range. Those ones could plain checks
or regular expressions checks


Like sequential expressions , range block should have end: expression denoting the end of scope for range mode. If you forget to add end: in the end of range block , the range mode will apply for the rest of check rules


