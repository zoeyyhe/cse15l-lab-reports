# CSE 15L Lab Report 1


> All directory are set as default `/home`, if changes are made they will be indicated in the code block ahead of the code with `cd _directory_`


## cd
1. An example of using the command with no arguments.
```
[user@sahara ~]$ cd
[user@sahara ~]$
```
> cd is a command used for changing directory, if successfully ran without error occuring, no output will be given while a change in prompt will appear.
> If ran with no arguments, it indicates that not changes are made and it is not an error, therefore it outputs nothing and prompt remains the same.
> Not an error

2. An example of using the command with a path to a directory as an argument.
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ 
```
> As described earlier, by running cd with a path to a directory as an argument, if successfully ran, it will outputs nothing while a change in the prompt will appear.
> Not an error

3.An example of using the command with a path to a file as an argument.

```
[user@sahara ~/lecture1]$ cd README
bash: cd: README: Not a directory
```
> cd is a command used ONLY for directory changes, therefore by using it with a file as an argument will output error.
> Is an error


---

## ls
1. An example of using the command with no arguments.
```
[user@sahara ~]$ ls
lecture1
```
> ls is a command used for listing the files & folders in the given path, when no argument is given, ls will return the files & folders in the current path
> Not an error

2. An example of using the command with a path to a directory as an argument.
```
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
```
> As described above, in this case ls is used along with a path to a directory as an argument
> Not an error

**Another approach**
```
[user@sahara ~]$ ls lecture1/messages
en-us.txt  es-mx.txt  fr-ca.txt  zh-cn.txt
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ ls messages
en-us.txt  es-mx.txt  fr-ca.txt  zh-cn.txt
```

3.An example of using the command with a path to a file as an argument.
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ ls README
README
```
> In this case, ls lists the file itself since file is unlike folders, itelf is is the only file
> Not an error

---

## cat
1. An example of using the command with no arguments.
```
[user@sahara ~]$ cat
1
1
2
2
```
> cat is a command used to print the contents of one or more files given by the paths, when no argument is given, input will have no prompt before it and return will only ouput the input itself, CTRL+D was used to exit the cat command
> *Explaination given by online information: it reads data from its standard input and write them to its standard output
> Not an error

2. An example of using the command with a path to a directory as an argument.
```
[user@sahara ~]$ cat lecture1
cat: lecture1: Is a directory
```
> cat is ran with a path to a directory, since cat is used to print the contents and folders is not a file, therefore it shows an error that the given argument is a directory.
> Is an error

3.An example of using the command with a path to a file as an argument.
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ cat README
To use this program:

javac Hello.java
java Hello messages/en-us.txt
```
> cat is ran with a path to a file, therefore it print the contents stored in the given file
> Not an error

---
