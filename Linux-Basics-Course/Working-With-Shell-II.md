### What I Learned

# File Compression and Archiving

* du -sh lets us see disk usage ina  human readable text ie. 30MB or 4.0GB
* ls -lh shows us the long list of files in a directory or on a file to see the file perms and size.
* tar lets us create what are called archives
  - -cf lets us create and name our tarfile ie test.tar then submit the files we want archived after. 
  - tar -cf test.tar file1 file2 file3
  - tar -tf lets us see the contenets of an already made tar ball.
  - tar -xf lets us extract those files from a tar ball.
  - tar -zcf lets us create and name and also compress the tar ball to take up less disk space
* 3 Popular Compression Methods are:
  - bzip2 and bunzip2
  - gzip and gunzip
  - xz and unxz
* They use different compression algorithms and have varied file sizes after zipping.
* bzcat , zcat ,xcat let us concatenate compressed files.

# Searching for Files and Patterns

* locate file.extension - returns all paths with that pattern
  - depends on a db for the file name queries may not work on new files
  - manually update db with updatedb as sudo
* find /directory/path -name file.extension yields the resulting file paths that match that pattern.
* grep to search within files
  - grep keyword file.extension but this is CaseSensitive to the keyword
  - run with the -i flag to search for all keyword instances irregardless of case.
  - grep -r can search recursively within an entire directory. but keyword must be covered in quotes and you have to specificy the directory instead of a file.
  - grep -v lets us see all lines that DONT have a particular string.
  - grep -w lets us search not for the characters in that order but for the word itself as a litteral string.
  - grep -A'N' -keyword- lets us see the keyword and some number N of lines after that keyword.
  - grep -B'N' -keyword- lets us see the keyword and some number N of lines before that keyword.
  - You can combine the -A and -B flags to loot at very specific lines around the keyword.

# IO Redirection

* we can use > to redirect the stdout to a file
* we can also use >> to redirect this but as an appending change not replacement. needs to be in " "
* we can use 2> to push the stderr to a file.
* we can use 2>> to append.
* if you dont want to see the stderr you can 2> to /dev/null - the bit bucket
* We can use pipes to take the stdout of one cammond to funnel into another command as its stdin
* in cases where you want to see the output being added to a file add tee after a pipe.
* if you are appending us a -a flag after tee

# VI Editor

* run the vi command followed by a file
* 3 Modes
  - Insert
    - press i,I,A,a,o,O to enter insert mode
    - press escape to go back to command
  - Command (Start)
    - move around with arrow keys
      - can also use h-left k-up j-down l-right
    - go to a line then 'y y' to copy
    - use -p above a line to paste below cursor
    - use 'Z Z' to save
    - use 'x' to delete a specific character.
    - use 'd d' to delete an entire line.
    - use 'd 3 d'  to delete the current line and next 2.
    - use 'u' to undo changes
    - use 'ctrl+r' to redo
    - use '/(text)' to find character patterns in decending order and ? for acending
    - n moves down in / mode and N moves up in / mode. Reversed for ? mode
  - Last Line
    - press : to go to last line mode
    - used for saving the file
    - discarding changes
    - exit vi
    - use :w to write to the file and save
    - use :q to quit
    - use :wq to save and quit
    - use :q! to quit without saving


### What I Did

# Lab 1

* had to use find to locate files.
* redirected the output of the find to a another file
* had to use grep to search for a file in a directory
* redirected stderr on failed attempts to a file
* used zcat to read the conetents of a compressed file and redirected the output to another file.

# Lab 2 

* used vi to navigate around a text page using hjkl
* copy and replaced lines and delete them
* saved the edits to the file
* deleted chunks of lines
* undid and redid tasks.

### Important Notes
