## 編譯器（compiler）
```
編譯器是用來將高階語言轉換成組合語言 (或者是機器碼) 的工具程式。有了編譯器或直譯器，程式設計師才能用高階語言撰寫程式。

一個現代編譯器的主要工作流程如下：

原始碼（source code）→ 預處理器（preprocessor）→ 編譯器（compiler）→ 組譯程式（assembler）
→ 目的碼（object code）→ 連結器（linker）→ 執行檔（executables）
，最後打包好的檔案就可以給電腦去判讀執行了。
```

## 語法
```
PROG = STMTS
BLOCK = { STMTS }
STMTS = STMT*
STMT = WHILE | BLOCK | ASSIGN
WHILE = while (E) STMT
ASSIGN = id '=' E;
E = F (op E)*
F = (E) | Number | Id
```

## 執行結果
```
user@DESKTOP-96FRN6B MINGW64 /d/ccc/book/sp/code/c/02-compiler/03-compiler
$ make clean
rm -f *.o *.exe

user@DESKTOP-96FRN6B MINGW64 /d/ccc/book/sp/code/c/02-compiler/03-compiler
$ make
gcc -std=c99 -O0 lexer.c compiler.c main.c -o compiler

user@DESKTOP-96FRN6B MINGW64 /d/ccc/book/sp/code/c/02-compiler/03-compiler
$ ./compiler test/while.c
while (i<10) i = i + 1;

========== lex ==============
token=while
token=(
token=i
token=<
token=10
token=)
token=i
token==
token=i
token=+
token=1
token=;
========== dump ==============
0:while
1:(
2:i
3:<
4:10
5:)
6:i
7:=
8:i
9:+
10:1
11:;
============ parse =============
(L0)
t0 = i
t1 = 10
t2 = t0 < t1
goto L1 if T2
t3 = i
t4 = 1
t5 = t3 + t4
i = t5
goto L0
(L1)
```

## 指標 ( Pointer ）
```
指標（英語：Pointer），是程式語言中的一類資料類型及其物件或變數，用來表示或儲存一個記憶體位址
，這個位址的值直接指向（points to）存在該位址的物件的值。
```
![image](https://user-images.githubusercontent.com/55796905/123538299-cfed3f00-d766-11eb-9de6-04fb14680d7b.png)

### Example
```
#include <stdio.h>

int main(void) {
    int b = 2;

    printf("變數 b 的值：%d\n", b);
    printf("變數 b 的記憶體位址：%p\n", &b); //%p為印出地址的16進位表示法

    return 0;
}
```
### 註解
我們拿到一個地址，都是為了要去到這個地址上、以抓取上面的變數。
利用 C 語言中的另一個運算元「 * 」來做這件事
[資料來源](https://kopu.chat/2017/05/15/c%E8%AA%9E%E8%A8%80-%E8%B6%85%E5%A5%BD%E6%87%82%E7%9A%84%E6%8C%87%E6%A8%99%EF%BC%8C%E5%88%9D%E5%AD%B8%E8%80%85%E8%AB%8B%E9%80%B2%EF%BD%9E/)
