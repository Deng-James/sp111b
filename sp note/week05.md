# 虛擬機(Virtual Machine)
![image](https://user-images.githubusercontent.com/55796905/123539454-7425b480-d76c-11eb-9425-765b531e6034.png)
![image](https://user-images.githubusercontent.com/55796905/123539479-94ee0a00-d76c-11eb-9656-472149813121.png)
![image](https://user-images.githubusercontent.com/55796905/123539554-ebf3df00-d76c-11eb-8990-606552e5ffd4.png)

## JVM -- Java 的虛擬機
```
user@DESKTOP-96FRN6B MINGW64 /d/pmedia/陳鍾誠/課程/系統程式/06-vm/01-jvm (master)
$ javac HelloWorld.java

user@DESKTOP-96FRN6B MINGW64 /d/pmedia/陳鍾誠/課程/系統程式/06-vm/01-jvm (master)
$ java HelloWorld
Hello World!

user@DESKTOP-96FRN6B MINGW64 /d/pmedia/陳鍾誠/課程/系統程式/06-vm/01-jvm (master)
$ javap -c HelloWorld.class
Compiled from "HelloWorld.java"
class HelloWorld {
  HelloWorld();   
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: getstatic     #7                  // Field java/lang/System.out:Ljava/io/PrintStream;
       3: ldc           #13                 // String Hello World!
       5: invokevirtual #15                 // Method java/io/PrintStream.println:(Ljava/lang/String;)V
       8: return
}
```
![image](https://user-images.githubusercontent.com/55796905/123539370-ff527a80-d76b-11eb-8f9d-be2708bae071.png)
> 使用虛擬機的好處

![image](https://user-images.githubusercontent.com/55796905/123539399-1e510c80-d76c-11eb-96aa-bff60fc00aba.png)
![image](https://user-images.githubusercontent.com/55796905/123539523-c961c600-d76c-11eb-8ef2-3f5a0ed2e0fe.png)
> 虛擬機的架構
