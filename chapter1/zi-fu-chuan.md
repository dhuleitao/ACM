# 字符串的灵活性

scanf\("%s",s\);不能接受空格、TAB、回车

而gets\(s\)可以

字符串结束后自动加‘\0‘

```
if(scanf("%s",s)!=1)return false;
if(!strcmp(s,"()"))break;
int v;
sscanf(&s[1],"%d",&v);
addnode(v,strchr(s,',')+1);
```



