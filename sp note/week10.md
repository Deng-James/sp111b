# 作業系統
![image](https://user-images.githubusercontent.com/55796905/123548298-caa7e880-d796-11eb-8ef1-ba899bd099be.png)

## 單行程與多工系統
![image](https://user-images.githubusercontent.com/55796905/123548352-093da300-d797-11eb-987b-5fa06cd1eb01.png)


## 多工 
多工處理（英語：Computer multitasking）是指電腦同時執行多個程式的能力。多工的一般方法是執行第一個程式的一段代碼，儲存工作環境；再執行第二個程式的一段代碼，儲存環境；……恢復第一個程式的工作環境，執行第一個程式的下一段代碼……現代的多工，每個程式的時間分配相對平均。

## 協同式多工
![image](https://user-images.githubusercontent.com/55796905/123548415-4b66e480-d797-11eb-8b61-a130e63d4461.png)

## 行程
行程（英語：process），是指電腦中已執行的程式。行程曾經是分時系統的基本運作單位。在面向行程設計的系統（如早期的UNIX，Linux 2.4及更早的版本）中，行程是程式的基本執行實體；在面向執行緒設計的系統（如當代多數作業系統、Linux 2.6及更新的版本）中，行程本身不是基本執行單位，而是執行緒的容器。

## Memory Management(記憶體管理)

Program要執行的話，就必須要從硬碟中取出，帶到記憶體內才可以執行。
CPU能夠直接存取register跟memory的內容。Memory unit只能看到位置(address)跟要做什麼事的需求(read or data and write request)。Register或指令的運作通常都在CPU clock(或是更少)內完成。Main memory可能會花費數個CPU時間週期，造成stall(memory < register speed)，這時就需要cache的出現，他的速度介於兩者之間。
> address binding(地址的連結)：
程式在disk上需要來到memory才能執行，這時就會形成input queue。這些通常都會被load到記憶體的起始位置0000，但實際上不一定要用這個記憶體位置，或是已經有被使用了。簡單來說，位置在不同的地方有不同的表現方式：
- 一開始時，地址都只是一個象徵而已 -> 0000
- 編譯後(compile)，地址會連接到relocatable address -> 0010
- 最後經由linker或是loader，relocatable address會連接到absolute address(絕對地址) -> 7010

### 參考資料
[https://www.slideshare.net/ccckmit/10-73472927](https://www.slideshare.net/ccckmit/10-73472927)

[https://ithelp.ithome.com.tw/articles/10207187](https://ithelp.ithome.com.tw/articles/10207187)
