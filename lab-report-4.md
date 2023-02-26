# Lab Report 4 
<!-- For the lab report this week, reproduce the task from the competition on your own. For each numbered step starting right after the timer (so steps 4-9), take a screenshot, and write down exactly which keys you pressed to get to that step. For special characters like <enter> or <tab>, write them in angle brackets with code formatting. Then, summarize the commands you ran and what the effect of those keypresses were.

For example, when you run the tests, you might want to use the up arrow or Ctrl-R to access your bash history rather than typing in the full command with classpath, etc. You might say something like this accompanying the screenshot for running the tests:

Keys pressed: <up><up><up><up><enter>, <up><up><up><up><enter>

The javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java command was 4 up in the search history, so I used up arrow to access it. Then the java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore command was 4 up in the history, so I accessed and ran it in the same way.

Add this lab report to your Github Pages site, and submit a PDF of it as usual. -->

### **Log into ieng6**
Keys Pressed: \
```<ctrl+r> s <enter>```

The ssh command has been used many times, so it's stored in my bash history. With a simple search for ```s```, I'm able to access that command. 

![](https://cdn.discordapp.com/attachments/889055402765991946/1079532092569952297/Screenshot_2023-02-26_at_2.35.04_PM.png)

### **Clone your fork of the repository from your Github account**
Keys Pressed: \
 ```git clone <cmd+v> <enter>```  \
(Repo URL was already in clipboard)

I typed out git clone and then pasted the already copied repository URL to speed up the process.

![](https://cdn.discordapp.com/attachments/889055402765991946/1079532724886454412/Screenshot_2023-02-26_at_2.37.34_PM.png)

### **Run the tests, demonstrating that they fail**
Keys Pressed: \
```cd l <tab> <enter>``` \
```<ctrl+r> javac - <enter>``` \
```<ctrl+r> java - <enter>```

The first line becomes ```cd lab7/```. Tabbing allows bash to autocomplete the directory that I change into.  \
The second and third lines searche for bash history for the ```javac``` and ```java``` commands with the correct classpath respectively. \
They become: ```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java``` and ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests```

![](https://cdn.discordapp.com/attachments/889055402765991946/1079533123861225602/Screenshot_2023-02-26_at_2.39.09_PM.png)

### **Edit the code file to fix the failing test**
Keys Pressed: \
```nano Li <tab> .j <tab> <enter> ``` \
```<ctrl+w> while (index2 <enter>``` \
```<down>``` 2 times, ```<right>``` 8 times \
```<backspace> 2``` \
```<ctrl+o> <enter> <ctrl+x>```

The first line becomes ```nano ListExamples.java```. I allow for bash to autocomplete the file for me; it first completes to ```ListExamples```, since there is also a ```ListExamples.class``` file in the directory. Then, I clarify with ```ListExamples.j``` which is unique. \
Next, I search for ```while(index2``` in the file and fix the buggy line that may create an infinite while loop. \
Then, using ```<ctrl+o> <enter>``` I save the file and leave the nano editor with ```<ctrl+x>```

![](https://cdn.discordapp.com/attachments/889055402765991946/1079535268803137546/Screenshot_2023-02-26_at_2.47.41_PM.png)

### **Run the tests, demonstrating that they now succeed**

Keys Pressed: \
```javac L <tab> .j <tab> <enter> ``` \
```<up>``` x3 ```<enter>```

I compile the newly editted file with the ```javac``` command; similarly to before, I allow bash to autocomplete ```ListExamples.java```. The whole command is ```javac ListExamples.java``` \
Since we just ran the ```java -cp``` command earlier to run the Tester file, we can directly go back in our history to run it by pressing the ```<up>``` arrow keys. It should be: ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests``` 

![](https://cdn.discordapp.com/attachments/889055402765991946/1079536272026107964/Screenshot_2023-02-26_at_2.51.40_PM.png)


### **Commit and push the resulting change to your Github account**

Keys Pressed: \
```git add L <tab> .j <tab> <enter>``` \
```git commit -m “fixed” <enter>``` \
```git push <enter>``` \
Once again, I allow bash to autocomplete ```ListExamples.java```, which makes the first line ```git add ListExamples.java```. \
Then, I commit the added file with the message ```"fixed"```. \
Finally, I push the commit to GitHub with ```git push```. 
