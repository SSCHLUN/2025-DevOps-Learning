# Working With Shell 

### What I Learned

* whatis
  - one line description of what a command does

* man
  - more detail on what a command does aswell as syntax structure and options.
 
* --help or --h option
  - use cases and options can be listed for that specific command.

* apropos -keyword-
  - search through the man pages to look for a specific -keyword-.

* 
### What I Did

Lab 1: Working With Shell

  - Has you create mutiple directories in the home directory
  - Interact with the -p option: Useful for avoiding having to run multiple commands for nested directories.
  - Using the mv command to move files/directories between directories
  -   mv uses relative pathing so theres no need to use the entire absolute path for each directory.
  - Using the mv command to rename directories
  - the type command is also used to figure out what kind command we are working with.
  -   usr/bin/COMMAND means it is a binary file.
  -   COMMAND is aliased... means its a an alias
  -   COMMAND is a shell builtin means its built into the shell
  -   COMMAND is a function is a function 

### Important Notes

$ allows us to reference variables that are set in various files.

; to string mutiple commands in one go. But it takes the context from the previous 
  ie. If i run mkdir -p reptile/snake; mkdir reptile/frog
    the -p isnt needed in the second command becasue after the first command is ran the reptile dir exists.
