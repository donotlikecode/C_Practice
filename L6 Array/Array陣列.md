在 C 語言中，沒辦法直接用一個指令就將整個陣列印出來。因為 C 語言不提供內建的陣列輸出功能，只能通過 for 迴圈手動逐一印出每個元素。這是由於 C 語言的陣列特性，陣列名本身只是陣列第一個元素的指標，並沒有包含陣列長度資訊。

陣列具有相同型別的連續記憶體位置,每個陣列中的第一個元素是第零位元素

**EX6-1宣告array和初始化array**
```c
#include <stdio.h>

int main()
{
    //兩種initialization array的方法
    //只能在宣告的時候給值 如果已經給名稱沒有宣告裡面的東西 就只能用迴圈去用
    int a[5] = { 1, 3, 5, 7, 9 }; //多一個compiler就不給過了,電腦會幫陣列a預留5個元素的位置
    int b[] = { 2, 4, 6, 8, 10, 12 };
    int sum = 0;
    for (int i = 0 ; i < 5; i++) {
        sum = sum + a[i];
        printf("a%i=%i\n", i, a[i]);
        printf("b%i=%i\n", i, b[i]);
        printf("sum to ith element = %d", sum);
        puts("");
    }
    printf("a[0]+a[1]+a[2]=%d\n", a[0] + a[1] + a[2]);
    //
    char c1[] = "first";
    char c2[] = { 's', 'e', 'c', 'o', 'n', 'd', '\0' };
    printf("c1=%s\n", c1);
    printf("c2=%s\n", c2);

}
```
**EX6-2用計算初始化array與#Define前置處理器**
```
#include<stdio.h>
#define SIZE 5 //array的最大尺寸

int main(void)
{
    int s[SIZE]; //陣列s有SIZE個元素

    for (size_t j = 0; j < SIZE; ++j) //size_t 為一個資料型別,一個unsigned int,這個型別建議用來表示陣列大小與index的變數
    {
        s[j] = 2 + 2 * j;
    }
    
    printf("%s%13s\n", "Element", "Value");

    for (size_t j = 0; j < SIZE; ++j) {
        printf("%7u%13d\n", j, s[j]);
    }
}

```
