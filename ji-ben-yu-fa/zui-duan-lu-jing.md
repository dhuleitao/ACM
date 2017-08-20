# [hdu2544最短路](http://blog.csdn.net/hnuzengchao/article/details/7534690)

# 备注：\#define INF 0x3f3f3f3f

meset\(a,0x3f,sizeof\(a\)\);

# Dijkstra单源点最短路径

模板总结：

1、Dijkstra\(int n,int x\) int map\[110\]\[110\],dis\[110\],visited\[110\];  

```
2、for (i=1;i<=n;i++)  
{
dis[i]=map[1][i];
visited[i]=0;
}
visited[x]=1;
```

```
3、for (i=1;i<=n;i++)  //大循环
    {  
        min=INF;  
        for (j=1;j<=n;j++)  
        {  
            if(!visited[j] && dis[j]<min)  
            {  
                p=j;  
                min=dis[j];  
            }  
        }  
        visited[p]=1;  
        for (j=1;j<=n;j++)  
        {  
            if(!visited[j] && dis[p]+map[p][j]<dis[j])  
            {  
                    dis[j]=dis[p]+map[p][j];  
            }  
        }  
    }  


```

```
#include<iostream>  
#include<cstdio>  
#include<cstring>  
using namespace std;  
#define INF 0x3f3f3f3;  
int map[110][110],dis[110],visited[110];  

void Dijkstra(int n,int x)  
{  
    int i,p,j,min;  
    for (i=1;i<=n;i++)  
    {  
        dis[i]=map[1][i];  
        visited[i]=0;  
    }  
    visited[x]=1;  
    for (i=1;i<=n;i++)  
    {  
        min=INF;  
        for (j=1;j<=n;j++)  
        {  
            if(!visited[j] && dis[j]<min)  
            {  
                p=j;  
                min=dis[j];  
            }  
        }  
        visited[p]=1;  
        for (j=1;j<=n;j++)  
        {  
            if(!visited[j] && dis[p]+map[p][j]<dis[j])  
            {  
                    dis[j]=dis[p]+map[p][j];  
            }  
        }  
    }  

}  

int main()  
{  
    int n,m,i,j,a,b,t;  
    while(scanf("%d%d",&n,&m)!=EOF,n+m)  
    {  
        for (i=1;i<=n;i++)  
        {  
            for (j=1;j<=n;j++)  
            {  
                map[i][j]=INF;  
            }  
        }  
        for(i=1;i<=m;i++)  
        {  
            scanf("%d%d%d",&a,&b,&t);  
            map[a][b]=map[b][a]=t;  
        }  
        Dijkstra(n,1);  
        printf("%d\n",dis[n]);  
    }  
    return 0;  
}
```

# Flyod所有顶点之间的最短路径

模板总结：

```
for (k=1;k<=n;k++)
{
for (i=1;i<=n;i++)
{
for (j=1;j<=n;j++)
{
if (dis[i][j]>dis[i][k]+dis[k][j])  
{
dis[i][j]=dis[i][k]+dis[k][j];
}
}
}
}
```

```
#include <iostream>  
#include <cstdio>  
using namespace std;  
const int INF=0x3f3f3f3f;  
int dis[110][110];  
int main()  
{  
    int i,j,k,n,m,p,q,s;  
    while(scanf("%d%d",&n,&m)!=EOF,n+m)  
    {  
        for (i=1;i<=n;i++)  
        {  
            for(j=1;j<=n;j++)  
            {  
                dis[i][j]=INF;  
            }  
        }  
        for (i=0;i<m;i++)  
        {  
            scanf("%d%d%d",&p,&q,&s);  
            dis[p][q]=dis[q][p]=s;        
        }  
        for (k=1;k<=n;k++)  
        {  
            for (i=1;i<=n;i++)  
            {  
                for (j=1;j<=n;j++)  
                {  
                    if (dis[i][j]>dis[i][k]+dis[k][j])  
                    {  
                        dis[i][j]=dis[i][k]+dis[k][j];  
                    }  
                }  
            }  
        }  
        printf("%d\n",dis[1][n]);              
    }  
    return 0;  
}
```



