title: "List comprehension+Map"
date: 2015-04-18 22:12:54
tags: [python,List comprehension,python map]
categories: [python,senior]
---

List comprehension
S = { 2*x | x ∈ (1..100) , x^2 >3 }

```
S = [2 * x for x in range(101) if x ** 2 > 3]
[mapping-expression for element in source-list if filter-expression]
```






```
## python -mtimeit -s'xs=range(10)' 'map(hex, xs)'
100000 loops, best of 3: 4.86 usec per loop
#python -mtimeit -s'xs=range(10)' '[hex(x) for x in xs]'
100000 loops, best of 3: 5.58 usec per loop

## python -mtimeit -s'xs=range(10)' 'map(lambda x: x+2, xs)'
100000 loops, best of 3: 4.24 usec per loop
#python -mtimeit -s'xs=range(10)' '[x+2 for x in xs]'
100000 loops, best of 3: 2.32 usec per loop
```

```
## python -mtimeit -s'i=[1000,2000,3000]' 'j=[10,20,30]' '[m + n for m, n in zip(i ,j)]'
1000000 loops, best of 3: 1.23 usec per loop

## python -mtimeit -s'i=[1000,2000,3000]' 'j=[10,20,30]' 'list(map(int.__add__, i, j))'
1000000 loops, best of 3: 1.79 usec per loop
```
[ref][]
[ref]:http://stackoverflow.com/questions/1247486/python-list-comprehension-vs-map