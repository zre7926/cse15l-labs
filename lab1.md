Lab Report 1 - Remote Access and FileSystem (Week 1)
========
Ryan Zhang 

cd
--------
1. **no arg** <br> 
Output/Input (Working Repository: /home/lecture1/messages)
```
[user@sahara ~/lecture1/messages]$ cd
[user@sahara ~]$
```
* Running cd with no argument resulted in /home being set as the working directory.
* There is no error.
2. **directory arg** <br> 
Output/Input (Working Repository: /home)
```
[user@sahara ~]$ cd ./lecture1
[user@sahara ~/lecture1]$ 
```
* Running cd with a path to a directory as an argument resulted in that directory being set as the working directory.
* There is no error.
3. **file arg** <br> 
Output/Input (Working Repository: /home)
```
[user@sahara ~]$ cd lecture1/Hello.class
bash: cd: lecture1/Hello.class: Not a directory
```
* Running cd with a path to a file as an argument resulted in an error.
* This is because you can't change the working directory to a file since it is not a directory.
<br>

ls
--------
1. **no arg** <br> 
Output/Input (Working Repository: /home/lecture1)
```
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
```
* Running ls with no argument resulted in the names of all the files and directories of the working directory being printed out in a row.
* There is no error.
2. **directory arg** <br> 
Output/Input (Working Repository: /home/lecture1)
```
[user@sahara ~/lecture1]$ ls messages
en-us.txt  es-mx.txt  hu.txt  zh-cn.txt
```
* Running ls with a path to a directory as an argument resulted in the names of all the files and directories of that directory being printed out in a row.
* There is no error.
3. **file arg** <br> 
Output/Input (Working Repository: /home/lecture1)
```
[user@sahara ~/lecture1]$ ls Hello.java
Hello.java
```
* Running ls with a path to a file as an argument resulted in the relative path of that file being printed out.
* There is no error.
<br>

cat
--------
1. **no arg** <br> 
Output/Input (Working Repository: /home)
```
[user@sahara ~]$ cat
input
input
lecture1 
lecture1
```
* Running cat with no argument resulted in a "mode" where the terminal repeatedly outputs whatever is inputted.
* There is no error.
2. **directory arg** <br> 
Output/Input (Working Repository: /home)
```
[user@sahara ~]$ cat lecture1
cat: lecture1: Is a directory
```
* Running cat with a path to a directory as an argument resulted in an error.
* This is because you can't print out a directory since it is not a file.
3. **file arg** <br> 
Output/Input (Working Repository: /home/lecture1/messages)
```
[user@sahara ~/lecture1/messages]$ cat en-us.txt 
Hello World!
```
* Running cat with a path to a file as an argument resulted in the content of that file being printed out.
* There is no error.
