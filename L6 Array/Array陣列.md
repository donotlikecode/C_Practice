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
```c
#include<stdio.h>
#define SIZE 5 //array的最大尺寸

int main(void)
{
    int s[SIZE]; //陣列s有SIZE個元素

    for (size_t j = 0; j < SIZE; ++j) //size_t 為一個資料型別,一個unsigned int,這個型別建議用來表示陣列大小與index的變數
    {
        s[j] = 2 + 2 * j;
    }
    
    printf("%s%13s\n", "Element", "Value");  //%13s(在這裡指的是Value)代表最少占 13 個字元寬度，若字串長度不足，會在左側補空格

    for (size_t j = 0; j < SIZE; ++j) {
        printf("%7u%13d\n", j, s[j]);
    }
}

```

**EX6-3array的典型應用:分析整理某項調查中收集的資料**
要求40位學生對自助餐廳的食物打分數,分數為1~10分(1是差,10是棒棒)
```c
#include<stdio.h>
#include<stdlib.h>
#include<time.h>
#define RESPONSES_SIZE 40 //array的尺寸
#define FREQUENCY_SIZE 11 

int main(void)
{
    int frequency[FREQUENCY_SIZE] = { 0 };//全部都會被設為0,
    //int responses[RESPONSES_SIZE] = { 1 + rand() % 10 }; //在 C 語言中，陣列的初始化只能在宣告時指定固定的值，不能直接用 rand() 給定每個元素的隨機值。
    int responses[RESPONSES_SIZE];
    srand(time(NULL));
    for (int i = 0; i < RESPONSES_SIZE; i++) {
        responses[i] = 1 + rand() % 10;
    }

    for(int i = 0; i < RESPONSES_SIZE; i++)
    printf("cousomer %d's rating is %d\n", i+1 ,responses[i]);

    //從response陣列中一次取出一個回應,將frequency陣列中的10個計數器(frquency[1]、frquency[2]、...、frquency[10])中的某一個增加1
    for (size_t answer = 0; answer < RESPONSES_SIZE; answer++)
    {
        ++frequency[responses[answer]];  //根據response[answer]的值來遞增適當的frquency計數器
    }
    printf("%s%17s\n", "Rating", "Frquency");

    for (size_t rating = 1; rating < FREQUENCY_SIZE; rating++)
    {
        printf("%6d%17d\n", rating, frequency[rating]);
    }
}
```
