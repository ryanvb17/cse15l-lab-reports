# Lab Report 3
---
## find command-line options
### 1. Use ``` -type f ``` to search for files only
via: https://linuxhandbook.com/find-command-examples/

example 1:
```
  $ find ./technical -type f -name "*med*"
```
By using this input we ask the computer to find any file in the ```./technical``` directory that has med in its name.
Without the ```-type f``` option, we would expect to see the directory ```./technical/biomed```, but with this option,
we get the following:
```
./technical/plos/pmed.0020273.txt
./technical/plos/pmed.0020065.txt
...
./technical/plos/pmed.0020242.txt
```
Every file containing ```med``` in its name is returned, and while there were many more files returned,
I decided not to take 30 lines just to show the other files, as the main point of this example is that
the ```./technical/biomed``` directory does not get returned as well, showing how this method could be useful.

example 2:
```
  $ find ./technical -type f -name "*11*"
```
Here is a similar example, where we are searching for files only with ```11``` somewhere in their name.
This should omit the directory ```./technical/911report``` and sure enough, here's what it returns:
```
./technical/government/Gen_Account_Office/gg96118.txt
./technical/government/Gen_Account_Office/July11-2001_gg00172r.txt
...
./technical/911report/chapter-11.txt
```
Once again, I've taken most of the files out to make this easier to read, but we can see that while one of the files
from the ```./technical/911report``` directory is shown, the directory itself is not.

### 2. Use ``` -type d ``` to search for directories only
via: https://linuxhandbook.com/find-command-examples/

example 1:
```
  $ find ./technical -type d -name "*med*"
```
Here we have a similar example to the first one, only this time we are looking for directories only.
Instead of getting the huge list of files like from the last command this time the output looks like this:
```
./technical/biomed
```
As you can see this option can be very useful, especially for people who use similar naming conventions for
the files they keep in a directory. This will allow you to find the directory much easier than just searching
for anything with ```med``` in its name.

example 2:
```
  $ find ./technical -type f -name "*11*"
```
This example is once again a familiar one. Just like with the first example, we would expect this to only return
the directory, and here's the output that it gives:
```
./technical/911report
```
Once again this cuts the output down majorly from what we would get without this option.

### 3. Use ``` -size ``` to search for anything of a certain size within the directory
via: https://linuxhandbook.com/find-command-examples/

example 1:
```
  $ find ./technical -size +250k
```
This command searches for anything above 250 kb in size. This option can be very useful for finding large files
that take up lots of space on your computer. With this option, ```k``` is used for kb, ```M``` for mb and ```G``` is used for gb,
with the ```+``` specifying the search for files at or above that size. Let's see what this returns:
```
./technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
./technical/government/Gen_Account_Office/d01591sp.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-3.txt
```
As you can see, in this directory there aren't many files above 250 kb, but if you were looking to save space,
removing these could save you could save over a mb of space.

example 2:
```
  $ find ./technical -size -1k
```
Here the command is looking for anything below 1 kb in space. This could be useful for finding small or
unfinished files. The ```-``` indicates that we are looking for files at or below that size.
Lets see what it returns:
```
./technical
./technical/government
./technical/government/About_LSC
./technical/government/Env_Prot_Agen
./technical/government/Alcohol_Problems
./technical/government/Post_Rate_Comm
./technical/plos/pmed.0020191.txt
./technical/plos/pmed.0020226.txt
./technical/911report
```
As you can see this will return a few directories as well, as they do not take up much space. If you want,
try combining this with ```-type f``` to search only for files meeting the size requirement.

### 4. Use ``` -maxdepth 1 ``` to search for anything only in the current directory
via: https://linuxhandbook.com/find-command-examples/

example 1:
```
  $ find ./technical -maxdepth 1 -name "*med*"
```
Here we can see that we are once again searching for anything with med in its name. This time, however,
we are only searching for things in the current directory. Heres the output of this command:
```
./technical/biomed
```
As you can see, this is another way to find the ```biomed``` directory without also seeing all
of the files with ```med``` in their name. If there were files within ```./technical``` that had
```med``` in their name, they would also show up, but there are not any in this case.

example 2:
```
  $ find ./technical -maxdepth 1 -name "*11*"
```
Once again we can see that the search is for anything with ```11``` in its name. This time we can see
if any of the files with this name are in the ```./technical``` directory, though.
Heres the output of this command:
```
./technical/911report
```
This tells us once again that the only thing with```11``` in its name in this directory is the ```911report```
directory, which could be very useful if you were looking for something in the current directory, but didn't want
anything in the below directories to also show up.
