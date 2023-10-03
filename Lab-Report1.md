# Lab Report 1

## cd command
Executing cd with no arguement caused the orginal directory was inside of lecture1, but after excuting cd without an arguement it went back to just the user file directory:
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$ 
```
After excuting cd with the lecture1 directory as the arguement, it added /lecture1 to the end of the directory path:
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



<br />
