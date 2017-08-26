\#include &lt;stdio.h&gt;

\#include &lt;algorithm&gt;

using namespace std;

int main\(\){

    int n;

    while\(scanf\("%d",&n\)&&n\){

        int a\[1000\];

        for\(int i=0;i&lt;n;i++\){

            scanf\("%d",&a\[i\]\);

        }

        sort\(a,a+n\);//可以自行测试一下删除后的结果

        do{

            for\(int i=0;i&lt;n;i++\)

                printf\("%d ",a\[i\]\);

            printf\("\n"\);

        }while\(next\_permutation\(a,a+n\)\);

    }

    return 0;

}

