# 硬币问题

p39挑战程序设计竞赛

```
const int V[6]={1,5,10,50,100};
int C[6];//输入
int A;
void solve(){
  int ans=0;
  for(int i=5;i>0;i--){
  int t=min(A/V[i],C[i]);
  A-=t*A/V[i];
  ans+=t;
  }
  printf("%d\n",ans);
}
```

# 区间问题

```
const int MAX_N=100000;
int N,S[MAX_N],T[MAX_N];
pair<int,int> itv[MAX_N];
void solve(){
  for(int i=0;i<N;i++)
  {
  itv[i].first=T[i];
  itv[i].secind=S[i];
  }
  sort(itv,itv+N);
  int ans=0,t=0;
  for(int i=0;i<N;i++){
  if(t<itv[i].second){
  ans++;
  t=itv[i].first;
  }
  }
  printf("%d\n",ans);
}
```



