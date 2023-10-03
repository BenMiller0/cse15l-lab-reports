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
Running the cat command with no arguement did not really throw an error, but nothing happened because it had nothing to add together:
```
[user@sahara ~]$ cat
```
Running cat with just a directory as an arguement resulted in an error with a message telling the user that lecture 1 is a directory, so the cat command cannot be ran on it:
```
[user@sahara ~]$ cat lecture1
cat: lecture1: Is a directory
[user@sahara ~]$
```
Not an error. Running cat with a .java printed all of the code within the file.
```
[user@sahara ~/lecture1]$ cat Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }
}
[user@sahara ~/lecture1]$
```


<br />
