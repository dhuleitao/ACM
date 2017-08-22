# 1、哈夫曼编码

#### 任何字符编码都不是其它字符编码的前缀：前缀编码

### 先建哈夫曼树，再进行编码

```
//函数<1>:创建权值数组为w的赫夫曼树HT,并求出n个字符的赫夫曼编码HC
void MakeHufm(HuffmanTree &HT,HuffmanCode &HC,long *w,int n)
{int m,x1,x2,i=0,j=0,start,c,f;
long m1,m2;
 HuffmanTree p; //赫夫曼树HuffTree的初始化
m=2*n-1;//郝夫曼树节点个数
 HT=(HuffmanTree)malloc((2*n)*sizeof(HTNode));
 for(p=HT,i=0,j=0;i<n;++i,++p,w++,j++) //给前n0个单元初始化
  {
	p->weight=*w;p->CH=j;p->parent=0;
   p->left=0;p->right=0;}
 for(;i<m;++i,++p)//对叶子之后的存储单元清零
  {p->weight=0;p->parent=0;
   p->left=0;p->right=0;}
 for(i=n;i<m;++i)//建赫夫曼树
 {m1=m2=MaxV;
  x1=x2=0;
  for(j=0;j<i;j++)//重点在于要找出两个最小的结点
  {if(HT[j].weight<m1&&HT[j].parent==0)
    {m2=m1;
     x2=x1;
     m1=HT[j].weight;
     x1=j;
    }
   else if(HT[j].weight<m2&&HT[j].parent==0)
    {m2=HT[j].weight;
     x2=j;
    }
  }
  HT[x1].parent=i;HT[x2].parent=i; //将找出的两棵权值最小的子树合并为一棵子树
  HT[i].left=x1;HT[i].right=x2;
  HT[i].weight=HT[x1].weight+HT[x2].weight;
 }
 //从叶子到根逆向求每个字符的赫夫曼编码
 HC=(HuffmanCode)malloc((n+1)*sizeof(char *));//头指针
 //分配求编码的工作空间
 char *cd=(char *)malloc(n*sizeof(char));
 cd[n-1]='\0';//编码结束符
 for(i=0;i<=n;++i)//逐个字符求赫夫曼编码
 {start=n-1;//编码结束符位置
  //从叶子到根逆向求编码
  for(c=i,f=HT[i].parent;f!=0;c=f,f=HT[f].parent)
   if(HT[f].left==c) cd[--start]='0';
   else cd[--start]='1';
  //为第i个字符编码分配空间
  HC[i]=(char *)malloc((n-start)*sizeof(char));
  strcpy(HC[i],&cd[start]);//复制编码
 }
 free(cd);  }

```



