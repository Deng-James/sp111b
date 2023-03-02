## stderr2.c
- code

```
#include <stdio.h>
#include <unistd.h>
#include <fcntl.h>

int main()
 {
  int fdb = open("log.txt", O_CREAT|O_RDWR, 0644);
  dup2(fdb, 2);
  fprintf(stderr, "Warning: xxx\n");
  fprintf(stderr, "Error: yyy\n");
}
```
- output

```
ubuntu@foo1:~/sp/08-posix/04-fs/04-stderr$ ./stderr2
ubuntu@foo1:~/sp/08-posix/04-fs/04-stderr$ ls
README.md  error.txt  log.txt  output.txt  stderr1.c  stderr2  stderr2.c
ubuntu@foo1:~/sp/08-posix/04-fs/04-stderr$ error.text
error.text: command not found
ubuntu@foo1:~/sp/08-posix/04-fs/04-stderr$ cat error.text
cat: error.text: No such file or directory
ubuntu@foo1:~/sp/08-posix/04-fs/04-stderr$ cat error.txt
Warning: xxx
Error: yyy
ubuntu@foo1:~/sp/08-posix/04-fs/04-stderr$ cat log.txt
Warning: xxx
Error: yyy
ubuntu@foo1:~/sp/08-posix/04-fs/04-stderr$
```

## blocking.c
- code

```
#include<sys/types.h>
#include<sys/stat.h>
#include<fcntl.h>
#include<unistd.h>
#include<stdio.h>
#include<stdlib.h>

int main(int argc, char* argv[])
{
    int fd = open("/dev/tty",O_RDONLY); //Open the standard I / O file, which is blocked.
    if(fd == -1){
        perror("open /dev/tty");
        exit(1);
    }
    int ret = 0;
    char buf[1024] = {0};
    while(1)
    {
        ret = read(fd, buf, sizeof(buf));
        if(ret == -1){
            perror("read");
            exit(1);
        }
        else if(ret == 0)
            printf("buf is null\n");
        else if(ret > 0)
            printf("buf is %s\n",buf);
        printf("test\n");
        sleep(1);
    }
    close(fd);

    return 0;
}
```

- output

```
ubuntu@foo1:~/sp/08-posix/07-nonblocking$ gcc blocking1.c -o blocking1
ubuntu@foo1:~/sp/08-posix/07-nonblocking$ ./blocking1
-------------------------------等待指令回復---------------------------------------
sda                                                 
buf is sda

test
```

## nonblocking.c
- code

```
#include<sys/types.h>
#include<sys/stat.h>
#include<fcntl.h>
#include<unistd.h>
#include<stdio.h>
#include<stdlib.h>

int main(int argc, char* argv[])
{
    int fd = open("/dev/tty", O_RDONLY | O_NONBLOCK); // O ﹣ Nonblock set file input and output to non blocking
    if(fd == -1){
        perror("open /dev/tty");
        exit(1);
    }
    int ret = 0;
    char buf[1024] = {0};
    while(1){
        ret = read(fd, buf, sizeof(buf));
        if(ret == -1){
            perror("read /dev/tty"); // fputs(stderr, "read /dev/tty")
            printf("no input,buf is null\n");
        }
        else {
            printf("ret = %d, buf is %s\n",ret, buf);
        }
        sleep(1);
    }
    close(fd);

    return 0;
}
```

- output

```
ubuntu@foo1:~/sp/08-posix/07-nonblocking$ gcc nonblocking1.c -o nonblocking1
ubuntu@foo1:~/sp/08-posix/07-nonblocking$ ./nonblocking1
read /dev/tty: Resource temporarily unavailable
no input,buf is null
read /dev/tty: Resource temporarily unavailable
no input,buf is null
read /dev/tty: Resource temporarily unavailable
no input,buf is null
sdadread /dev/tty: Resource temporarily unavailable
no input,buf is null

asdret = 5, buf is sdad


ret = 4, buf is asd


sad
ret = 4, buf is sad


read /dev/tty: Resource temporarily unavailable
no input,buf is null
read /dev/tty: Resource temporarily unavailable
no input,buf is null
read /dev/tty: Resource temporarily unavailable
no input,buf is null
sad
ret = 4, buf is sad


read /dev/tty: Resource temporarily unavailable
no input,buf is null
dread /dev/tty: Resource temporarily unavailable
no input,buf is null
s
ret = 3, buf is ds



read /dev/tty: Resource temporarily unavailable
no input,buf is null
s
ret = 2, buf is s
```
