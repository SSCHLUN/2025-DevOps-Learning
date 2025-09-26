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
  

### What I Did

### Important Notes
