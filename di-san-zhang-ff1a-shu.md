基本概念：

满二叉树、完全二叉树、树的度，节点的度

二叉树的性质：

![](/assets/import7.png)

![](/assets/import8.png)

性质3：对任意一棵二叉树T，若叶结点数为n0，而其度为2的结点数为n2，则n0=n2+1

性质4：具有n个结点的完全二叉树的深度为 ![](/assets/import5.png)

# ![](/assets/import6.png)

# 树的路径长度：树中所有结点的路径长度之和；一般记为PL。

# 结点的带权路径长度：从根到该结点的路径长度与该结点权的乘积；

# 树的带权路径长度也称为树的代价。



# 1、中序非递归遍历二叉树

```
void InOrder ( BinTree T ) 
{
    stack S;   InitStack( &S );    //递归工作栈
    BinTreeNode *p = T;           //初始化
    while ( p != NULL || !StackEmpty(&S) ) {
	if( p != NULL ) 
            { Push(&S, p);   p = p->leftChild; }
        else{         
            Pop(&S, p);                         //退栈
            printf( p->data) ;   //访问根
            p = p->rightChild;               
        } //if
    } //while
 return ok;
} //InOrder
```



