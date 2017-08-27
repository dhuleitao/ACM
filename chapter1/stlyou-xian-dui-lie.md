bool empty\(\) const;    //判断优先级队列是否为空，为空返回true，否则返回false

size\_type size\(\) const;    //返回优先级队列中的元素个数

const value\_type& top\(\) const\(\);    //返回优先级队列中第一个元素的参考值。

void push\(const value\_type& x\);    //把元素x插入到优先级队列的尾部，队列的长度加1

void pop\(\);    //删除优先级队列的第一个值，前提是队列非空，删除后队列长度减1

**priority\_queue&lt;Type,**[**Container**](http://lib.csdn.net/base/docker)**, Functional&gt;**

如果我们把后面俩个参数缺省的话，优先队列就是大顶堆，队头元素最大。（这点由上面的程序可以看出）

```
其实就三种用法

第一种，直接使用默认的。

它的模板声明带有三个参数，priority_queue<Type, Container, Functional>
Type 为数据类型， Container 为保存数据的容器，Functional 为元素比较方式。
Container 必须是用数组实现的容器，比如 vector, deque 但不能用 list.
STL里面默认用的是 vector. 比较方式默认用 operator< , 所以如果你把后面俩个
参数缺省的话，优先队列就是大顶堆，队头元素最大。
看例子


priority_queue<int> qi;

    int a[len] = {3,5,9,6,2};

    priority_queue<int> qi;
    for(i = 0; i < len; i++)
        qi.push(a[i]);

    for(i = 0; i < len; i++)
    {
        cout<<qi.top()<<" ";
        qi.pop();
    }

通过<操作符可知在整数中元素大的优先级高。
故例子中输出结果为：9 6 5 3 2

第二种：

第二种方法：
在示例1中，如果我们要把元素从小到大输出怎么办呢？
这时我们可以传入一个比较函数，使用functional.h函数对象作为比较函数。

如果要用到小顶堆，则一般要把模板的三个参数都带进去。
STL里面定义了一个仿函数 greater<>，对于基本类型可以用这个仿函数声明小顶堆
priority_queue<int, vector<int>, greater<int> >qi2;

对于自定义类型，则必须自己重载 operator< 或者自己写仿函数

#include <iostream>
#include <queue>

using namespace std;

struct Node{
    int x, y;
    Node( int a= 0, int b= 0 ):
        x(a), y(b) {}
};

bool operator<( Node a, Node b ){
    if( a.x== b.x ) return a.y> b.y;
    return a.x> b.x; 
}

int main(){
    priority_queue<Node> q;

    for( int i= 0; i< 10; ++i )
    q.push( Node( rand(), rand() ) );

    while( !q.empty() ){
        cout << q.top().x << ' ' << q.top().y << endl;
        q.pop();
    }

    getchar();
    return 0;
}



或者这样定义也是能达到效果的：

struct Node{
    int x, y;
    Node( int a= 0, int b= 0 ):
        x(a), y(b) {}

    friend operator<( Node a, Node b ){
    if( a.x== b.x ) return a.y> b.y;
    return a.x> b.x;

    }
};

自定义类型重载 operator< 后，声明对象时就可以只带一个模板参数。
但此时不能像基本类型这样声明
priority_queue<Node, vector<Node>, greater<Node> >;
原因是 greater<Node> 没有定义，如果想用这种方法定义
则可以按如下方式

例子:

#include <iostream>
#include <queue>

using namespace std;

struct Node{
    int x, y;
    Node( int a= 0, int b= 0 ):
        x(a), y(b) {}
};

struct cmp{
    bool operator() ( Node a, Node b ){
        if( a.x== b.x ) return a.y> b.y;

        return a.x> b.x; }
};

int main(){
    priority_queue<Node, vector<Node>, cmp> q;

    for( int i= 0; i< 10; ++i )
    q.push( Node( rand(), rand() ) );

    while( !q.empty() ){
        cout << q.top().x << ' ' << q.top().y << endl;
        q.pop();
    }

    getchar();
    return 0;
}

还有一点要注意的是priority_queue中的三个参数，后两个可以省去，因为有默认参数，不过如果，有第三个参数的话，必定要写第二个参数。
```



