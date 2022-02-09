
## Code change #1

First, we ran into this fun problem.

![this bad boy](img\badfileresult1.png)


The problem
with this markdown parses was that we were able to easily confuse it, making it think that there was an extra link that wasn't there. 


[This](https://github.com/fighterkabir/markdown-parse/commit/0e05f82551ef8c36d66acbe3d82309b472dfdd9d) 
the accused file, which sucessfully broke it. The actual solution to this problem was fairly simple, we just added a loop that checked for "https" before a link, and included that. 

Before the fix, the code would be confused at the excessive open and closed parenthses, resulting in the added link of "[(((((((((((". The solution to said problem was to check for "https" beforehand, because that would make sure that only actual links (ie. not gibberish) would be included into the list of links



![This bad boy](img\failedtestfile.png)







## Code change 2


![bad pictures](img\badfileresult2.png)

Next, we had this less than fun break. 

[This](https://github.com/fantasticfishman/markdown-parse/commit/5c75bdd0f93c274757cfc52fb43b521f0a53cd9c)
file was confusing the parser, so that it would add [k!] into the link itself, causing an issue. The solution was to create an if statement looking for "(" after we had found one, and if we found another, to set that as the new open parenthese.

![fixed picture](img\fixedfile7.png)



## Code change 3

![bad image](img\badfileresulttest4.png)

The final bug I had to fix was a bug where the code wouldn't correctly find the link. More specifically, putting any text between a ")" and a "[" would normally break the link, but with the parser it didn't matter. 

[This file](https://github.com/Ripslash/markdown-parse/blob/main/test-file(4).md)
caused the problem, but thankfully I was able to fix it with the code below

![the fixed image](img\fixedfile5.png)

The code adds a statement that if the next "(" wasn't immediately after a "]", it should look for a new link starting at the "]". This means that having text between the "]" and "(" wouldn't break the program anymore