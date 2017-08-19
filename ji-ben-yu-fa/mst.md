求最小生成树有多方法，常用的有两种：

![](/assets/import1.png)

```
Prime算法特点：将顶点归并，与边数无关，适于稠密网，时间复杂度O(N2)。Kruskal算法特点：将边归并，适于求稀疏网的最小生成树O(eloge2e)    
```

## **概念：**

在[无向图](https://baike.baidu.com/item/%E6%97%A0%E5%90%91%E5%9B%BE/1680427)中，如果从顶点vi到顶点vj有路径，则称vi和vj连通。如果图中[任意](https://baike.baidu.com/item/%E4%BB%BB%E6%84%8F/26806)两个顶点之间都连通，则称该图为[连通图](https://baike.baidu.com/item/%E8%BF%9E%E9%80%9A%E5%9B%BE/6460995)

，否则，称该图为非连通图，则其中的极大连通子图称为连通分量，这里所谓的极大是指子图中包含的顶点个数极大。



在[有向图](https://baike.baidu.com/item/%E6%9C%89%E5%90%91%E5%9B%BE/1852743)中，若图中[任意](https://baike.baidu.com/item/%E4%BB%BB%E6%84%8F/26806)两个顶点vi和vj都连通，则称为[强连通图](https://baike.baidu.com/item/%E5%BC%BA%E8%BF%9E%E9%80%9A%E5%9B%BE/6769617)。有向图的最大[强连通](https://baike.baidu.com/item/%E5%BC%BA%E8%BF%9E%E9%80%9A/1131406)子图称为该有向图的[强连通分量](https://baike.baidu.com/item/%E5%BC%BA%E8%BF%9E%E9%80%9A%E5%88%86%E9%87%8F/7448759)。强连通图只有一个强连通分量，即本身，非强连通图有多个强连通分量。任何[连通图](https://baike.baidu.com/item/%E8%BF%9E%E9%80%9A%E5%9B%BE/6460995)的连通分量只有一个，即为其本身。

# 模板总结：

1、数据结构

```
struct road
{
int a,b,len;
}x[max];//图上的两点和边
int per[max];//根节点
int cnt;//计数新图的边是否为n-1
int kase;//标记是否合并

```

2、函数

```
void init()//初始化函数  
{  
    for(int i=1;i<=m;++i)  
    {  
        per[i]=i;  
    }  
} 
int cmp(road a,road b)  
{  
    return a.len<b.len;  
}  
int find(int x)//查找函数  
{  
    int r=x;  
    while(r!=per[r])  
    {  
        r=per[r];  
    }  
    int i=x,j;  
    while(i!=r)  
    {  
        j=per[i];  
        per[i]=r;  
        i=j;  
    }  
    return r;  
}
void join(int a,int b)//合并函数  
{  
    int x=find(a),y=find(b);  
    if(x!=y)  
    {  
        per[y]=x;  
        kase=1;//标记变量  
        ++cnt;//边数累加  
    }  
}  
int main()  
{  
    int a,b,c,i,sum;  
    while(~scanf("%d%d",&n,&m),n)  
    {  
        cnt=sum=0;init();  
        for(i=0;i<n;++i)  
        {  
            scanf("%d%d%d",&a,&b,&c);  
            x[i].a=a;x[i].b=b;x[i].len=c;//输入保存  
        }  
        sort(x,x+n,cmp);//排序  
        for(i=0;i<n&&cnt<m-1;++i)//遍历查找  
        {  
            kase=0;  
            join(x[i].a,x[i].b);//合并  
            if(kase)//是否连入集合  
            {  
                sum+=x[i].len;  
            }  
        }  
        if(cnt==m-1)//生成了最小权值的树  
        {  
            printf("%d\n",sum);  
            continue;  
        }  
        printf("?\n");  
    }  
    return 0;  
}     
```



