## sed command
A stream editor for filtering and transforming text.
### Basic
In gerenal, `sed` opreates on a stream of text that it reads from either standard input or from a file. and it prints stream to standard out by default. Unless you redirected, `sed` will print its output to the screen instead of saving it in a file.
***
### Syntax
The basic syntax of sed is :
```
sed [OPTION]... {script only if no other script} [input-file]...
//More concise syntax
sed [options] {opreation command} [file]
```
***
#### Usage 
Some useful usages of `sed` base on some real examples are as follow:
##### Print
First, We create a file to practice this commmand. And using `cat` to view the contents of the file we created.
```bash
echo "here is a test_file of sed" > test_file.txt
echo "This is the second line of test_file.txt" >> test_file.txt
cat test_file.txt
here is a test_file of sed
This is the second line of test_file.txt
```
We know that `sed` print its output to the screen by default. So if we have no opreation on text which should be edited, the `sed` command works as a file reader. Opreations is contained in single quotes of `sed`'s command. Now we put nothing in single quotes and see  its effects.
```bash
sed '' test_file.txt
here is a test_file of sed
This is the second line of test_file.txt
```
Honestly, `sed` has explicit `print` command, which is specified by using the `p` character within single quotes. Let's try it.
```bash
sed 'p' test_file.txt
here is a test_file of sed
here is a test_file of sed
This is the second line of test_file.txt
This is the second line of test_file.txt
```
As above shows, You will see that `sed` operates line by line. It accepts a line, opreate on it, and outputs the resulting text before repeating the process on the next line. `sed` has printed each line twice. This is because it automatically prints each line, and then we've told it to print explicitly with the `p` command.  We can ues `-n` option ,which suppresses the automatic printing:
```bash
sed `p` -n test_file.txt
here is a test_file of sed
This is the second line of test_file.txt
```
***
##### Modify
At first, It is important to note here that our source file is not being affected. It is still intact. The edits are output to our screen by default. If we want to save our edits, we can redirect standard output to a file like so:
```
sed [options] {opreation command} [source_file_to_edit] > [dst_file_to_save]
```
***
###### Substitute
You can change one word to another word by using the explicit command `substitute`, which is defined by using the `s` character within single quotes. 
```
's/old_word/new_word'
```
The three slashes `/` are used to separate the different text fields. You can use other characters to delimit the fields if it would be more helpful.
For instance, if we were tring to change a website name, using another delimiter would be helpful since URLs contain slashes. 
```bash
echo "http://www.example.com/index.html" | sed 's_com/index_org/home_
http://www.example.org/home.html
```
Now, Let's create a file to practice susbstitutions.
```
[jiangdi@example ~]$ cat test 
This is a big test for my sed test.
This is fewtest for my sed test.
```
Now substitute the expression "test" with "change".
```
[jiangdi@example ~]$ sed 's/test/change/' test
This is a big change for my sed test.
This is fewchange for my sed test.
[jiangdi@example ~]$ 
```
As above shows, The `test`  within `fewtest` is changed to `fewchange`. Besides, the second `test` is not changed. This is because by default, the `s` command operates on the first match in a line and then moves to the next line.if we want to make `substitute` opreate on every `test`, we can add an optional flag to the `substitute` command.
```
[jiangdi@example ~]$ sed 's/test/change/g' test
This is a big change for my sed change.
This is fewchange for my sed change.
```
If we only wanted to change the second instance of "on" that sed finds on each line, then we could use the number "2" instead of the "g".
```
[jiangdi@example ~]$ sed 's/test/change/2' test
```
if we want the search process to ignore case, we can pass it the "i" flag.
```
[jiangdi@example ~]$ sed 's/test/change/i' test
```
***
If you wish to find more complex patterns with regular expressions, we have a number of different methonds of referencing the matched pattern in the replacement text.
###### Delet
we can easily perform text deletion where we previously were specifying were specifying text printing by changing the `p` command to the `d` command.
```
[jiangdi@example ~]$ cat test 
This is a big test for my sed test.
This is fewtest for my sed test.
[jiangdi@example ~]$ sed 'd' test 
[jiangdi@example ~]$ sed '1d' test 
This is fewtest for my sed test.
[jiangdi@example ~]$ sed '2d' test 
This is a big test for my sed test.
```
### Reference Reading
1. [sed(1) - Linux man page](https://linux.die.net/man/1/sed)
2. [The Basics of Using the Sed Stream Editor to Manipulate Text in Linux](https://www.digitalocean.com/community/tutorials/the-basics-of-using-the-sed-stream-editor-to-manipulate-text-in-linux)
3. [Sed Command in Linux/Unix with examples](https://www.geeksforgeeks.org/sed-command-in-linux-unix-with-examples/)
***