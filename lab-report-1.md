# Lab Report 1

## Install VS Code
- Install Visual Studio Code at [https://code.visualstudio.com/](https://code.visualstudio.com/)
- Open the Application
- A window should open that looks like this: 
![Image](https://cdn.discordapp.com/attachments/1062889449396129903/1062889741416153209/Screenshot_2023-01-11_at_4.24.18_PM.png)
In my case, VS Code was already installed, so there are Recent directories listed.

## Remotely Connecting
- Look up your CSE 15L Account at [https://sdacs.ucsd.edu/~icc/index.php](https://sdacs.ucsd.edu/~icc/index.php)
- Use the "_Forgot Username or New Student?_" section and follow instructions to changing your password (this may take 15 minutes to update).
- Open Terminal on VS Code and type in the following command where xxxx is replaced by your course specific account's characters: 
```
$ ssh cs15lxxxx@ieng6.ucsd.edu
```
- Terminal should respond with something that looks like this:
![Image](https://cdn.discordapp.com/attachments/1062889449396129903/1062892496868360292/Screenshot_2023-01-11_at_4.35.15_PM.png)
- Respond with yes and type in your password (your password won't show but it is keeping track of your keystrokes)

## Trying Some Commands
- You can try some commands like 
- `ls` which lists all the commands in the working directory
- `cd [directory]` which changes the workign directory to `[directory]`
- Explore the directories in the server; for example, I tried accessing a random directory:
![Image](https://cdn.discordapp.com/attachments/1062889449396129903/1063726335832358972/Screenshot_2023-01-13_at_11.48.36_PM.png)
