# 检测有向环的一种方法是对AOV网络构造他的拓扑有序序列

模板总结：

1、topo函数最重要的两个循环-查找入度为0的，把与它相连的点的入度减1或置0（注意表示方法）

2、遍历顶点，拓扑排序成功则输出

```
#include<stdio.h>
#include<string.h>
#define N 505

int n, m;
int vis[N], map[N][N];

int topo(int k){
    for (int i = 1; i <= n; i++)
        if (map[k][i])
            return 0;
    for (int i = 1; i <= n; i++)
        map[i][k] = 0;
    return 1;
}

int main(){
    while (scanf("%d%d", &n, &m) != EOF){
        // Init.
        memset(vis, 0, sizeof(vis));
        memset(map, 0, sizeof(map));
        int cnt = 0;

        // Read.
        for (int i = 0; i < m; i++){
            int a, b;
            scanf("%d%d", &a, &b);
            map[b][a] = 1;
        }

        // topo.
        while (cnt != n){
            for (int i = 1; i <= n; i++){
                if (vis[i])
                    continue;
                else if (topo(i))
                {
                    printf("%d", i);
                    vis[i] = 1;
                    cnt++;
                    break;
                }
            }
            if (cnt < n)
                printf(" ");
            else
                printf("\n");
        }
    }
    return 0;}
```

# uva 1423 - Guess（拓扑排序）    升级



