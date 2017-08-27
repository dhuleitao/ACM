背包九讲

```
#include<stdio.h>  
#include<string.h>  
#include<algorithm>  
using namespace std;  
const int maxn= 3500;  
int w[maxn],p[maxn],dp[12880];  
int main()  
{  
    int n,c;  
    while(~scanf("%d%d",&n,&c))  
    {  
        memset(dp,0,sizeof(dp));  
        for(int i=0; i<n; i++)  
            scanf("%d%d",&w[i],&p[i]);  
        for(int i=0; i<n; i++)  
            for(int j=c; j>=w[i]; j--)  
                dp[j]=max(dp[j],dp[j-w[i]]+p[i]);  
        printf("%d\n",dp[c]);  
    }  
}
```



