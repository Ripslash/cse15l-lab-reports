## Option 3

Copying whole directories recursively is easy, and fun. Just use the -r before your directory to copy the whole thing! 

The command should look something like this
``` 
scp -r . cs15lwi22aun@ieng6.ucsd.edu:~\
```

During the running of the code, this huge amount of code will transmit, mostly files you aren't supposed to read 

Looks a little like this

![image!](img\midcopy.png)


Then I can run all the tests on the ieng6 directory, like this

![imag]( img\finishedtesters.png)


With the combination of this and semicolons, we can actually upload everything, then run the tests in one huge command!

This massive command looks like this!
```
scp -r . cs15lwi22aun@ieng6.ucsd.edu:~/; ssh cs15lwi22aun@ieng6.ucsd.edu "/software/CSE/oracle-java-se-14/jdk-14.0.2/bin/javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar MarkdownParseTest.java; /software/CSE/oracle-java-se-14/jdk-14.0.2/bin/java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore MarkdownParseTest" 
```

Okay, I'll break it down.
The first part is just the scp command, followed by the ssh command.

In the quotation marks, we have the commands for compiling and running the tests, and this is where things get a little more confusing.

The ieng6 servers aren't configured to automatically run java from the right place, so we have to specify where we are getting our java from. 

That leads to this command instead of javac
```
software/CSE/oracle-java-se-14/jdk-14.0.2/bin/javac
```
and something similar for java.

Then, it's just compiling the testers in the normal JUnit way. 

All combined though, it's the longest command of my life, and it ends with this

![imag](img\finishedbeegcommand.png)

(the .016 seconds is the JUnit, not the length of the whole command)