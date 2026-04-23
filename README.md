# Examples for sparrow.ai bot

# Q1 Hello word

Question:

I have a text with "hello world" string, please create task.check to verify
the text contains the string

Answer

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

I have a text with "hello world" string, please create task.check to verify
the text contains the string, case insensitive

Answer

```
regexp: :i "hello world"
```

Explanation:

Task check dsl uses so called regular expression checks to verify some data contains some strings
matching Regular expressions. In this example we use so called regular expression modifier
(:i) to enable case insensitive matching. Raku regular expression should be placed
after reserved `regxp: ` prefix.

# Q3 Sequential checks 

I have a text with numbers 1,2,4,5 going back to back ,
so that every number takes exactly one line:

1
2
3
4
5

Please create task.check to verify
the text contains those number going back to back sequentially 

Answer

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


