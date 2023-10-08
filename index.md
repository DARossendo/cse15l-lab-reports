# CD
---
** -cd (no argument) **
...
- the working directory was the the main class, in the is case was lecture 1. I'm assuming why I got this output, being sent to the beginning of the file, it
seems it wants to read or change to a directory, but when it has no  argument it changes to the first instance of the file which was *lecture_1*. This is not an error, as it 
doesn't consist of an error message
...

** -cd (directory argument) **
...
the working directories were the directories that were given such as lecture 1 and messages. For this instance, it changed directories to those. However,
when I tried to *cd* to a text file it gave me an error as it was *not a directory*. To *cd* to a directory it does work. 
...

** -cd (file argument) **
...
The working directories were * lecture 1 * and * messages *. When I cd to a file within the *lecture 1* directory, I received an error stating that such a directory
did not exist. The output that I received was an error on my part as it demonstrated that the file was not a directory and that I was in the incorrect directory to begin
with.
...

#ls
---

** -ls (no argument) **
...
The working directories were home and its content. When I ls without an argument, it displays my current directory. For example when I was at /home/ it displayed
*lecture 1* and when I cd into the directory and then *ls* I got the content in the directory. This shows no errors and does not provide any errors.
...

** -ls (directory argument) **
...
The working directory was /home/lecture_1. For this if I *ls* to a specific directory it will give the content of that directory regardless of my location. I was able to
*ls* from /home/lecture1 with ease into other directories and get its content just fine with no errors.
...

**-ls (file argument)**
...
The working directory was /home/lecture1/messages. For this, I *ls* a random file within the directory which didn't return the directory, but the name of the file.
I believe this is not an error as I believe *ls* gives information of descriptors of directory/file.
...

#cat
---

** -cat (no argument) **
...
Working directories was /home/. Without an argument, *cat* simply seems to double anything that was typed and entered. For example, when I typed cleared the system
simply repeated the same values. I believe this is not an error as it might be used to test code.
...

** -cat (directory argument)**
...
Working directories were /home/lecture1. With a directory argument, it simply prints out the name of the directory and states that is a directory. 
...

**-cat (file argument)**
...
