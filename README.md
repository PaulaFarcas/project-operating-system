# project-for-lab-at-operating-system



Requirments:

Write a C program, which uses system calls and library functions in Unix, that takes multiple arguments representing paths to regular files / directories / symbolic links.

The program provides the following functionalities: 



The program will pass through all the arguments

For each file, depending on the file type, the name of the file and the type of the file will be displayed and after that an interactive menu will be displayed, with all the options available for that specific file type.

The user should then, input the desired options for that file from the keyboard, as a single string. The options will be preceded by the ‘-’ sign and will contain multiple letters corresponding to each option. An example input from the keyboard looks like this: -nal. Note that, some options may require additional input information. 

After entering the options string, the information about that file will be printed to the standard output.

If one of the letters of the string is not a valid option an error message will be displayed and the menu will appear again. 

A) Regular file: name (-n), size (-d), hard link count (-h), time of last modification (-m), access rights (-a), create symbolic link (-l, this will wait for user input for the name of the link). The access rights will be displayed in the format:

B) Symbolic link: name (-n), delete symbolic link (-l), size of symbolic link (-d), size of target file (-t), access rights (-a). Note that if that the -l option is given, the other following options will no longer be performed

C) Directory: name (-n), size (-d), access rights (-a), total number of files with the .c extension (-c)


The parent process will create for each argument one child process that will handle the options introduced by the user (for each file type we have the corresponding options). Additionally to this child process, the parent process will create a second child process, whose functionality will be:

If the argument is a regular file with the .c extension, the second child will execute a script. 

Script requirement: Having a regular file with the .c extension given as argument, the script should compile the file and print at standard output the number of errors and the number of warnings.
If the argument is a regular file but doesn't have the .c extension, the second child should print the number of lines

If the argument is a directory, the second child process will execute a command for creating a file with the .txt extension and a specific name (e.g. <dir_name>_file.txt, where <dir_name> is the name of the directory)

If the argument is a symbolic link, the second child process will execute a command for changing the permissions of the symbolic link as it follows:

read, write and execution rights for the user

read and write rights for the group (no execution rights should be granted for the group of user!)

no read, write or execution rights for other users

The parent process must properly receive the return state of its child processes and print the following message "The process with PID <PID> has ended with the exit code <EXIT_CODE>".

For each argument, the created processes must run in parallel with each other


