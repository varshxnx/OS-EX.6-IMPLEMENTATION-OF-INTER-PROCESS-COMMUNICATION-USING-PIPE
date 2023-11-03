# OS-EX.6-IMPLEMENTATION-OF-INTER-PROCESS-COMMUNICATION-USING-PIPE
## AIM:

Write C programs to illustrate IPC using pipes mechanisms.

## ALGORITHM:

1. Create a child process using fork().
2. Create a simple pipe with C, we make use of the pipe() systemcall.
3. Create two file descriptor fd[0] is set up for reading, fd[1] is set up for writing.
4. Close the read end of parent process using close() and perform write operation.
5. Close the write end of child process and perform reading.
6. Display the text.
## PROGRAM:
```c
#include <stdio.h>
 #include<stdlib.h>
 #include<string.h>
 #include<sys/types.h>
 #include<sys/wait.h>
 #include<unistd.h>
int main()
{
int fd[2],child; char a[10];
printf("\n Enter the string:");
scanf("%s",a);
pipe(fd);
child=fork();
if(!child)
{
close(fd[0]);
write(fd[1],a,5); wait(0);
}
else
 {close(fd[1]);
read(fd[0],a,5);
printf("The string received from pipe is: %s",a);
}
return 0;
}
``` 
## OUTPUT:
![image](https://github.com/Shrruthilaya-Gangadaran/OS-EX.6-IMPLEMENTATION-OF-INTER-PROCESS-COMMUNICATION-USING-PIPE/assets/93427705/57c44e40-2088-4ea5-9c7a-507b74da961c)

## RESULT: 
Thus, IPC using pipes mechanism is illustrated using C program successfully.
