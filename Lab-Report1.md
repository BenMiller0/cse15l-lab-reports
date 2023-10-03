# Lab Report 1

## cd command
Not an error. Executing cd with no arguement caused the orginal directory was inside of lecture1, but after excuting cd without an arguement it went back to just the user file directory:
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$ 
```
Not an error. After excuting cd with the lecture1 directory as the arguement, it added /lecture1 to the end of the directory path which was orginally just the user:
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$
```
Running cd with a file as the arguement caused what appears to be an error message to be displayed telling the user that the given file is not an arguement. This is because cd cannot take a specific file as an arguement:
```
[user@sahara ~/lecture1]$ cd Hello.java
bash: cd: Hello.java: Not a directory
```
## ls command
Not an error. Running ls while inside of the lecture1 directory, it listed all of the files within the lecture1 directory:
```
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
[user@sahara ~/lecture1]$
```
Running ls with the lecture1 directory as an arguement while already being inside lecture1 resulted in an error because the system could not file that directory while it was already inside of it:
```
[user@sahara ~/lecture1]$ ls lecture1
ls: cannot access 'lecture1': No such file or directory
[user@sahara ~/lecture1]$
```
Executing ls with Hello.java did not result in an error, but it did strangley just return the name of the file back:
```
[user@sahara ~/lecture1]$ ls Hello.java
Hello.java
[user@sahara ~/lecture1]$
```
## cat command

<br />
