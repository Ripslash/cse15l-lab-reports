Nothing is here yet!

Create another page in your lab report repository, like you did for lab report 1, and write your report there.

Pick three code changes that your group worked on in labs 3 and 4 in order to fix a bug; these should be stored as commits on someone’s repository. Fork the repository so you have your own copy with all the work your group did if you haven’t already.

For each of the three code changes:

Show a screenshot of the code change diff from Github (a page like this)
Link to the test file for a failure-inducing input that prompted you to make that change
Show the symptom of that failure-inducing input by showing the output of running the file at the command line for the version where it was failing (this should also be in the commit message history)
Write 2-3 sentences describing the relationship between the bug, the symptom, and the failure-inducing input.
You will submit this to the week 4 lab report assignment on Gradescope, which will have a similar process to the first lab report for grading.


## Code change #1

First, we ran into this fun problem.

![this bad boy](img\badfileresult1.png)


The problem
with this markdown parses was that we were able to easily confuse it, making it think that there was an extra link that wasn't there. 


[This](https://github.com/fighterkabir/markdown-parse/commit/0e05f82551ef8c36d66acbe3d82309b472dfdd9d) 
the accused file, which sucessfully broke it. The actual solution to this problem was fairly simple, we just added a loop that checked for "https" before a link, and included that. 

![This bad boy](img\failedtestfile.png)

## Code change 2


![bad pictures](img\badfileresult2.png)


Need the while loop to fix this!

[this](https://github.com/fantasticfishman/markdown-parse/commit/5c75bdd0f93c274757cfc52fb43b521f0a53cd9c)