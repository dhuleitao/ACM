### uva 536 Tree Recovery （前序，中序变后序）

```cpp
#include <stdio.h>
#include <string.h>
#define N 1005
char *move = NULL;
char str[N], sum[N];

void reback(int a, int b){
    if (a == b)    return ;
    for (int i = a; i < b; i++){
    if (sum[i] == *move){
        move++;
        reback(a, i);
        reback(i + 1, b);
        putchar(sum[i]);
        return;
    }
    }
}

int main(){
    while (scanf("%s%s", str, sum) != EOF){
    move = str;
    reback(0, strlen(sum));
    printf("\n");
    }
    return 0;}
```

#  uva 548 - Tree 中序后序建树



