## stderr2.c

- code

```
#include <stdio.h>
#include <unistd.h>
#include <fcntl.h>

int main() {
  int fdb = open("log.txt", O_CREAT|O_RDWR, 0644);  
  dup2(fdb, 2); // 複製 fdb 檔案描述子到 2 (stderr)
  fprintf(stderr, "Warning: xxx\n");
  fprintf(stderr, "Error: yyy\n");
}
```
- output

```
ubuntu@sp109:~/sp/08-posix/04-fs/04-stderr$ gcc stderr2.c -o stderr2
ubuntu@sp109:~/sp/08-posix/04-fs/04-stderr$ ./stderr2
ubuntu@sp109:~/sp/08-posix/04-fs/04-stderr$ ls
README.md  log.txt     stderr1    stderr2
error.txt  output.txt  stderr1.c  stderr2.c       
ubuntu@sp109:~/sp/08-posix/04-fs/04-stderr$ cat log.txt 
Warning: xxx
Error: yyy
```


## telnet

- code

```
ubuntu@sp109:~/sp/08-posix/06-net/03-telnet1$ ./server&
[1] 8114
ubuntu@sp109:~/sp/08-posix/06-net/03-telnet1$ ./client
connect to server 127.0.0.1 success!
127.0.0.1 $ ls
cmd=ls
Makefile
README.md
client
client.c
server
server.c

127.0.0.1 $

```
## helloWebServer
```
user@user-myubuntu:~/sp/08-posix/06-net/05-http$ make
gcc -std=c99 -O0 helloWebServer.c ../net.c -o helloWebServer
gcc -std=c99 -O0 headPrintServer.c ../net.c -o headPrintServer
gcc -std=c99 -O0 htmlServer.c ../net.c httpd.c -o htmlServer
user@user-myubuntu:~/sp/08-posix/06-net/05-http$ ./helloWebServer 
Server started at port: 8080
0:got connection, client_fd=4
1:got connection, client_fd=4
```

## htmlServer
```
user@user-myubuntu:~/sp/08-posix/06-net/05-http$ ./htmlServer 
Server started at port: 8080
===========header=============
GET / HTTP/1.1
Host: localhost:8080
User-Agent: curl/7.68.0
Accept: */*


path=/
not html => no response!
===========header=============
GET /index.html HTTP/1.1
Host: localhost:8080
User-Agent: curl/7.68.0
Accept: */*


path=/index.html
path contain .htm
responseFile:fpath=./web/index.html
===========header=============
GET /hello.html HTTP/1.1
Host: localhost:8080
User-Agent: curl/7.68.0
Accept: */*


path=/hello.html
path contain .htm
responseFile:fpath=./web/hello.html
```
