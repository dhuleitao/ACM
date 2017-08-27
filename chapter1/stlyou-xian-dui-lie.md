bool empty\(\) const;    //判断优先级队列是否为空，为空返回true，否则返回false

size\_type size\(\) const;    //返回优先级队列中的元素个数

const value\_type& top\(\) const\(\);    //返回优先级队列中第一个元素的参考值。

void push\(const value\_type& x\);    //把元素x插入到优先级队列的尾部，队列的长度加1

void pop\(\);    //删除优先级队列的第一个值，前提是队列非空，删除后队列长度减1

