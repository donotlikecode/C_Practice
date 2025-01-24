在 C 語言中，沒辦法直接用一個指令就將整個陣列印出來。因為 C 語言不提供內建的陣列輸出功能，只能通過 for 迴圈手動逐一印出每個元素。這是由於 C 語言的陣列特性，陣列名本身只是陣列第一個元素的指標，並沒有包含陣列長度資訊。

**EX7-1宣告array和初始化array**
```c
#include <stdio.h>

int main()
{
    //兩種initialization array的方法
    //只能在宣告的時候給值 如果已經給名稱沒有宣告裡面的東西 就只能用迴圈去用
    int a[5] = { 1, 3, 5, 7, 9 }; //多一個compiler就不給過了
    int b[] = { 2, 4, 6, 8, 10, 12 };
    for (int i = 0; i < 5; i++) {
        printf("a%i=%i\n", i, a[i]);
        printf("b%i=%i\n", i, b[i]);
        puts("");
    }

    //
    char c1[] = "first";
    char c2[] = { 's', 'e', 'c', 'o', 'n', 'd', '\0' };
    printf("c1=%s\n", c1);
    printf("c2=%s\n", c2);

}

```
