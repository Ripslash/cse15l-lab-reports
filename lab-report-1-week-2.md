## Week 1 Lab Report

During week one, we spent our lab time setting up our coding environments and worked on creating an easy-to-use remote environment. 

### **Step 1**: Download VSCode.
 Super easy first step, you just have to go to 
[this link]( https://code.visualstudio.com) and click download.


After finishing the download process and opening up VSCode, you should see an environment similar to this
![The Environment](img/base_VSCODE.PNG)


### **Step 2**: Remote Connection
Firstly, we have to get OpenSSH installed. Using
[this](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) link, install OpenSSH. 

Then, use [this](https://sdacs.ucsd.edu/~icc/index.php) link to get to the UCSD course account lookup page, where you can find your cs 15L account. 

It looks like cs15lwi22zz@ieng6.ucsd.edu, but zz is replaced with a unique combination, either 2 or 3 letters long. 

Given that this is directed toward past me, I'm going to write each command using my actual account.

When inside VSCode, you can click a Terminal button on the top left. Then hit Open New Terminal. From that new terminal, you can use regular commandline commands.

For example, type 

```
ssh cs15lwi22aun@ieng6.ucsd.edu
```
into the command line to attempt to login to the IENG6 Servers.

It's gonnas ask if you want to recongize this network, and the answer is yes!


After you put your password in, which is just your triton password, it should look like this

![thing](img/ieng6.PNG)

Now, you can run some fun commands!
```
cd, ls, mkdir, cp, cat
```
are all good examples of commands to mess around with. Personally, I used 

`ls - a`

and got this fun result

![Long list](img/testingCommands-lab1.PNG)


doing `-a` shows some of the hidden dotfiles, as well as the rest of the files. 

### **Step 3**: Copying Files

Now, you need to move commands from the client(local) to the server(remote). To do this, you're going to use the `scp` command, which will copy and paste files into the remote. 

The syntax looks like this

```
scp filename.java cs15lwi22aun@ieng6.ucsd.edu:~/
```

It should ask you for your password again, then if you log back in to the server with ssh, and use the ls command, you should be able to see your file in the server

Yay! Copying the file worked. Now we deal with the huge pain that is your password. Typing in the password every time you want to move a file or get into the system is a huge pain, so we are going to create something called an SSH key. 


### **Step 4:** SSH Keys and optimization 
The section about setting up an ssh key.

Okay, to be perfectly straight, this sucks on a windows computer. There was a long and painful process of setting this up, and I honestly don't remember how to do it. So, instead, I'm going to explain how it would work on a Linux Computer.

First, type,
```
ssh-keygen
```

Then hit enter on all of the other stuff, it doesn't matter for this.
Then, go onto the server itself, create a directory called .ssh through `mkdir`, and logout.

Then, copy this command, substituting your own personal info
```
scp /Classpath to .ssh on local device/.ssh/id_rsa.pub cs15lwi22aun@ieng6.ucsd.edu:~/.ssh/authorized_keys
```

and then you should be good!

It'll look like this:


![Post-Optimization](img/ssh-without-password-lab1.PNG)



After you've set up your key, then you can get into the realm of optimizing!



You can write code after your command line ssh to have it run immediately.



```
ssh cs15lwi22aun@ieng6.ucsd.edu "javac filename.java; java filename"
```

So, using a semicolon inbetween commands will run both commands on the same line, and having the quotes means that it wont break

For example, this doesn't do what you think it does. 

```
ssh cs15lwi22aun@ieng6.ucsd.edu javac filename.java; java filename
```
This will compile the file in the server, but will run in clientside, as the semicolon will have a new command. The quotes will keep the commands in one group so they'll all run remotely.

![Like this!](img/ssh-calling-whereami.PNG)

Once you've set this up, you can update the file on the server with supreme ease. In fact, let's count keystrokes.


 1) write the command out for the first time, including javac and java in quotes
 2) press up every time you want to redo the command.

 This means that you only have to type out the command once. And if you want to make it even faster, you can copy the file from a text document for even less steps. 

 2 keytrokes for Ctrl C, 2 for Ctrl V, one for enter. Cleans this up at 5 keystrokes max!

 

