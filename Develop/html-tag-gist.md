# Tutorial for Matching HTML Tag Regex

Welcome! In this guide, we will explore the /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/ regex.

Whether you're new to regular expressions like myself or want to expand your understanding, 
this tutorial will break down each component of the regex and explain its functionality.

## Summary

Regular expressions, often referred to as Regex, play a big role in string search algorithms. 
They are there to identify specific patterns within text, and this process is typically carried 
out using functions like FIND or FIND AND REPLACE.

To illustrate this concept, let's take a look at an example of searching for HTML tags in code:

/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/

This regular expression is specifically crafted to recognize HTML tags, 
whether they are opening tags or self-closing tags. It excels at extracting 
the tag name and, where relevant, any content enclosed within those tags.

It's essential to have an understanding of HTML tags, To make the 
most of this tutorial. As a quick refresher, HTML tags are enclosed within 
< and > symbols, forming both an opening and closing "tag." If you've ever 
inspected the source code of a web page, you've likely come across examples 
like < HTML >, < main >, < div >, and many others.

In the world of HTML, an important rule is that for every open tag, there must 
be a corresponding closing tag. This ensures that the code within the tags functions 
as intended. HTML tags can be more complex than the previous straightforward example, 
often incorporating distinct elements that execute specific tasks when the webpage is 
rendered. Take a moment to ponder this complexity:

< a href="http://www.MusicStuffs.com" title="This is MusicStuffs" target="_blank" >

Let's start by breaking down a link with the URL "http://www.MusicStuffs.com." When you 
hover your mouse over it, you'll notice the title "This is MusicStuff" appears. Additionally, 
it has the attribute "target="_blank"," which signifies that clicking the link will open 
a new browser window or tab, depending on the user's browser settings.

Because HTML tags can have a wide spectrum of characters, a regex string search needs 
to be flexible enough to account for alphanumeric characters as well as special characters.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
In Regex, anchors such as ^ and $ define the boundaries for a match within an input string. The caret ^ marks the start of the search, and the dollar $ denotes the end, ensuring that the regex pattern matches the entire string. In the context of the HTML tag regex /^<([ a-z ]+)([ ^< ]+)(?:>(.)</\1>|\s+/>)$, the opening < and closing > tags are anchored at the beginning and end of the pattern. This allows the system to locate < and > characters along with any content in between, whether it's alphanumeric or comprised of special characters.

### Quantifiers

Quantifiers specify how many times a character or group should appear. In this regex, + is a quantifier. + means "one or more," so [ a-z ] + matches one or more lowercase letters.

( + ) ensures that at least one lowercase letter is present in the tag name.
( * ) allows for the possibility of zero or more characters between the opening and closing HTML tags.

? - The question mark ? makes the preceding element in the regex optional. It can match it 0 or 1 time, indicating that the element is not required but can occur once.

*? - The *? combination makes the preceding quantifier (like *) match as few times as possible, unlike the default behavior where quantifiers tend to match as much as possible.

{7,9} - Curly braces with a range, like {7,9}, specify that the preceding element should occur between 7 and 9 times. In your example, it enforces a match with 7 to 9 characters.

These quantifiers are essential for making the regex pattern flexible enough to handle various HTML tag structures,
they provide flexibility and precision when defining matching criteria in regular expressions.

### OR Operator

The | symbol in regex acts like a Boolean OR operator. It enables you to define alternatives, causing the search to look for a match of either the preceding or following expression. For instance, in the regex pattern (?:>(.*)<\/\1>|\s+\/>), it uses the | operator to match either a closing tag or a self-closing tag.

### Character Classes

Character classes define a set of characters that can match a single character. 
[ a-z ] is a character class that matches any lowercase letter. We use it to capture the tag name.

### Flags

Regex flags are modifiers that alter regex behavior. Here are some common ones:

i makes the match case-insensitive.

g enables global matching, finding all matches in the input.

m is for multiline matching, considering the start and end of each line.

s performs a global search for whitespace characters.

While our regex doesn't use flags, remember that you can combine them, like gi for case-insensitive global matching.

### Grouping and Capturing

Parentheses () are used for grouping and capturing. In our Matching HTML regex, we use them to capture the tag name and the content within the tags.

### Bracket Expressions

A bracket expression in regex, enclosed in square brackets, matches a single character or collating element. When it starts with a circumflex ( ^ ), it becomes a complemented expression. For instance, [ a-z ] defines a character set. In our case, [ ^< ]+ captures one or more characters that are not the < character, used to extract content within tags.

### Greedy and Lazy Match

The * quantifier is greedy by default, meaning it matches as much as possible. To make it lazy (matching as little as possible), you can use *?. Our regex uses * for capturing content within tags.

### Boundaries

Boundaries, like \b, ensure matches occur at word boundaries. These boundaries are defined at three positions:

1. Before the first character in the string if it's a word character.

2. After the last character in the string if it's a word character.

3. Between two characters within the string, where one is a word character and the other isn't.

But our regex doesn't utilize boundaries because HTML tags typically don't align with these word boundaries.

### Back-references

In our regex, back-references, denoted as \1, help us ensure that the closing tag matches the opening tag. To do this, we capture text within a pair of parentheses using [ a-z ] [ a-z 0-9 ]*. \1 then checks that the text within these parentheses in the closing tag is identical to the opening tag. Additionally, the / character before \1 is a literal forward slash found in the closing HTML tag we aim to match.

### Look-ahead and Look-behind

Look-ahead and look-behind assertions ((?=...) and (?<=...)) allow you to specify conditions before or after a match. 

Our regex doesn't use look-aheads or look-behinds. The real difference is that they match characters and gives up the match. 

Returning the result: Match or no Match

## Author

Martin Lopez wrote this tutorial and can be foudn at https://github.com/emelmusica/module-17-regex/blob/main/Develop/html-tag-gist.md