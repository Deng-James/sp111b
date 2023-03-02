## fork1.c

- code

```
#include <stdio.h> 
#include <sys/types.h> 
#include <unistd.h>

int main()
 { 
    fork(); 
    fork(); 
    printf("%-5d : Hello world!\n", getpid());
}
```
- output

```
ubuntu@foo1:~/sp/08-posix/03-fork/01-hello$ 12372 : Hello world! 
12371 : Hello world!                                             
12373 : Hello world!                                             
./fork1                                                           
12374 : Hello world!    
```



## zombie.c

- code

```
#include <stdlib.h>
#include <sys/types.h>
#include <unistd.h>
int main ()
 {
  pid_t child_pid;
  /* Create a child process. */
  child_pid = fork ();
  if (child_pid > 0) 
  {
    /* This is the parent process. Sleep for a minute. */
    sleep (60);
  }
   else 
  {
    /* This is the child process. Exit immediately. */
    exit (0);
  }
  return 0;
}
```
- output

```
ubuntu@foo1:~/sp/08-posix/03-fork/05-zombie$ ./zombie&
[1] 12455
ubuntu@foo1:~/sp/08-posix/03-fork/05-zombie$ ps
    PID TTY          TIME CMD
  10092 pts/0    00:00:00 bash
  12455 pts/0    00:00:00 zombie
  12456 pts/0    00:00:00 zombie <defunct>
  12457 pts/0    00:00:00 ps
```



## myshell.c

- code

```
#include "../myshell.h"

int main(int argc, char *argv[])
 {
  char path[SMAX], cmd[SMAX];
  getcwd(path, SMAX-1); 
  while (1) 
  { 
    printf("myshell:%s $ ", path); 
    fgets(cmd, SMAX-1, stdin);     
    system(cmd);                  
  }
}

```

- output

```
ubuntu@foo1:~/sp/08-posix/05-myshell/v1$ ./myshell
myshell:/home/ubuntu/sp/08-posix/05-myshell/v1 $ ls
README.md  myshell  myshell.c
```
