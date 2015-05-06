title: "itertolls + DFS"
date: 2015-04-18 22:44:51
tags: [python,python itertolls]
categories: [python,senior]
---
程式 8個變數 範圍由1~2
輸出 8個變數全部相加 = 9的結果


```
x = 3
def DFS(data, deep):
    if deep==9:
        if sum(data)==9:
            print data
        return

    for i in range(1, x):
        DFS(data+[i], deep+1)

if __name__ == '__main__':
    DFS([], 1)
```

use itertools
```
import itertools
x = 3
if __name__ == '__main__':
    for data in itertools.product(range(1,x), repeat=8):
        if sum(data) == 9:
            print data
```

remove repeat
```
import itertools
x = 4
ans = set()
if __name__ == '__main__':
    for data in itertools.product(range(1,x), repeat=7):
        if sum(data) == 9:
            ans.add(tuple(sorted(data)))
    for i in ans:
        print i
```

```
import itertools
x = 4
if __name__ == '__main__':
    for data in itertools.combinations_with_replacement(range(1,x), 7):
        if sum(data) == 9:
            print data
```