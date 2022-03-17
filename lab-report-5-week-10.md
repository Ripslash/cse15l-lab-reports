## Lap Report 5

final one baybeeee

I found the bugs through a combination of manual looking up
and the diff command, as the diff command isolated what line the
differences in the error occurs. Then, I could go into the two documents
with the results to find the specific file, then I could go into
the file to find the specific test that broke.

### Test File # 22

The markdown file was this
```
 [foo](/bar\* "ti\*tle")
```

My Code was this,
```
 [/bar\* "ti\tle"]
```
and theirs was this:
```
Their Code: []
```

Clearly the given code is correct, as a URL with a backslash shouldn't be counted.
So, the main problem is that my code doesn't account for backslashes at all, which
is a pretty big problem when the thing preventing this code from working is a backslash. 

As you can see here in my code, there is no checker for a backlash, and that is why it broke
![the code](img\codeToFix.png)



### Test File # 578

The markdown file was this

```
My ![foo bar](/path/to/train.jpg  "title"   )
```

My Code was this,
```
 [/path/to/train.jpg "title"   ]
 ```
and theirs was this:
```
Their Code: []
```

Theirs is correct once again, but for a different reason. My code doesn't factor in images, or at least an exclamation point before a URL link. It stats as a fairly simple problem to solve but ends up getting really complex at the end. 

As you can see here in my code, there is no checker for an exclamation point, and that is why it broke
![the code](img\codeToFix.png)


Yes, its the same picture. No one responded to my issue comment on github! 