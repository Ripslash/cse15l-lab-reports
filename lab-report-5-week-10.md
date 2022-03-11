## Lap Report 5

final one baybeeee

I found the bugs through a combination of manual looking up
and the diff command, as the diff command isolated what line the
differences in the error occurs. Then, I could go into the two documents
with the results to find the specific file, then I could go into
the file to find the specific test that broke.


test file # 22
[foo](/bar\* "ti\*tle")

My Code: [/bar\* "ti\tle"]
Their Code: []


and also


test file # 578
My ![foo bar](/path/to/train.jpg  "title"   )

My Code: [/path/to/train.jpg "title"   ]
Thier Code: []


