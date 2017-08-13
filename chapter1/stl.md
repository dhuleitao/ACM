# 不定长数组vector

1 基本操作

\(1\)头文件\#include&lt;vector&gt;.

\(2\)创建vector对象，vector&lt;int&gt; vec;

\(3\)尾部插入数字：vec.push\_back\(a\);

\(4\)使用下标访问元素，cout&lt;&lt;vec\[0\]&lt;&lt;endl;记住下标是从0开始的。

\(5\)使用迭代器访问元素.

\(6\)插入元素：    vec.insert\(vec.begin\(\)+i,a\);在第i+1个元素前面插入a;

\(7\)删除元素：    vec.erase\(vec.begin\(\)+2\);删除第3个元素

vec.erase\(vec.begin\(\)+i,vec.end\(\)+j\);删除区间\[i,j-1\];区间从0开始

\(8\)向量大小:vec.size\(\);

\(9\)清空:vec.clear\(\);

3  算法

\(1\) 使用reverse将元素翻转：需要头文件\#include&lt;algorithm&gt;

reverse\(vec.begin\(\),vec.end\(\)\);将元素翻转\(在vector中，如果一个函数中需要两个迭代器，

一般后一个都不包含.\)

\(2\)使用sort排序：需要头文件\#include&lt;algorithm&gt;，

sort\(vec.begin\(\),vec.end\(\)\);\(默认是按升序排列,即从小到大\).

可以通过重写排序比较函数按照降序比较，如下：

定义排序比较函数：

bool Comp\(const int &a,const int &b\)  
{  
    return a&gt;b;  
}  
调用时:sort\(vec.begin\(\),vec.end\(\),Comp\)，这样就降序排序。

