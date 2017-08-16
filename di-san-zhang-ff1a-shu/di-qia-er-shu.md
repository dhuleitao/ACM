笛卡尔树

### poj 1785 Binary Search Heap Construction\(笛卡尔树）

```cpp
#include <stdio.h>
#include <string.h>
#include <algorithm>
using namespace std;
const int N = 105;
const int M = 50500;

struct node {
	char name[N];
	int val, l, r, fa;
}t[M];

bool cmp(const node& a, const node& b) {
	return strcmp(a.name, b.name) < 0;;
}

void insert(int in) {
	int j = in - 1;
	while (t[j].val < t[in].val) j = t[j].fa;

	t[in].l = t[j].r;
	t[t[in].l].fa = in;
	t[in].fa = j;
	t[j].r = in;
}

void put(int p) {
	if (!p) return;
	printf("(");
	put(t[p].l);
	printf("%s/%d", t[p].name, t[p].val);
	put(t[p].r);
	printf(")");
}

int main () {
	int n;
	while (scanf("%d", &n), n) {
		for (int i = 1; i <= n; i++)
			scanf(" %[a-z]/%d", t[i].name, &t[i].val);

		sort(t + 1, t + n + 1, cmp);
		t[0].val = 0x3f3f3f3f;
		t[0].r = t[0].l = t[0].fa = 0;

		for (int i = 1; i <= n; i++) {
			t[i].r = t[i].l = t[i].fa = 0;
			insert(i);
		}

		put(t[0].r);

		printf("\n");
	}
	return 0;
}
```



