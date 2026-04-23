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
