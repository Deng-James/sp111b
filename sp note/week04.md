## Linux 
```
Linux是一種自由和開放原始碼的類UNIX作業系統

Linux嚴格來說是單指作業系統的核心，因作業系統中包含了許多使用者圖形介面和其他實用工具。
```

## 下載虛擬機 vmware
## 安裝multipass

## if 複習
### code(判斷奇偶數)
```
#include <stdio.h>

int main(void) {
    int input = 0;
    int remain = 0;

    printf("輸入整數：");
    scanf("%d", &input);

    remain = input % 2;
    if(remain == 1) {
        printf("%d 為奇數\n", input);
    }
    else {
        printf("%d 為偶數\n", input);
    }

    return 0;
}
```
### output 
```
輸入整數：10
10 為偶數
```
