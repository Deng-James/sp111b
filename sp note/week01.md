## gcc使用方式

| 指令 | 註解 |
| --- | --- |
| -c  | 只做編譯(不做連結) |
| -S  | 輸出組譯碼 |
| -E  | 將預處理結果顯示 |
| -I  | 追加include檔案的搜尋路徑 |
| -L  | 追加library檔案的搜尋路徑 |
| -l  | 指定連結的函式庫 |
| -Wall | 顯示所有的警告訊息 |
| -g | 編入除錯資訊(要使用GDB除錯一定要加) |
| -O2 | 做最佳化 |
### Example:
```
gcc -o file a.c b.c c.c
gcc -Wall -g -o test test.c
gcc -Iinclude -Llibrary -lmy_lib -o test1 test1.c
gcc -DDEBUG_ON -o test2 test2.c
gcc -c -o test3 test.c
```
##### [gcc使用方式來源](https://omusico.pixnet.net/blog/post/25368607)


## makefile
> 編譯小型程式可用簡單的命令編譯或 shell script 編譯，但當程式很大且包含大量標頭檔和函式庫時，就需要使用 makefile。

| 指令 | 註解 |
| --- | --- |
| $@  | 指目標名稱 |
| $<  | 指第一個前提 |
| $^  | 指所有先決條件 |

- 目標 (Target) : 一個目標檔，可以是 Object 檔，也可以是執行檔，還可以是一個標籤。
- 依賴 (Dependency, Prerequisites) : 要產生目標檔 (target) 所依賴哪些檔。
- 命令 (Command) : 建立專案時需要執行的 shell 命令。命令部分的每行的縮進必須要使用 Tab 鍵而不能使用多個空格。

##### [makefile來源](https://mropengate.blogspot.com/2018/01/makefile.html)
