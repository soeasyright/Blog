title: "Read file and sort"
date: 2015-04-18 18:21:28
tags: [python,sort]
categories: [python,junior]
---
```
import random
class Student:
    def __init__(self,id,name,v1,v2,v3,v4,v5,rank):
        self.id = int(id)
        self.name = name
        self.v = []
        self.v.append(int(v1))
        self.v.append(int(v2))
        self.v.append(int(v3))
        self.v.append(int(v4))
        self.v.append(int(v5))

        self.rank = int(rank)

    def set_random(self,random):
        self.random = int(random)

    def set_club(self,club):
        self.club = int(club)


ins = open( "file.tsv", "r" )
students = []
for line in ins:
    tmp = line.split('\t')
    students.append( Student(tmp[1],tmp[2],tmp[3],tmp[4],tmp[5],tmp[6],tmp[7],tmp[8]) )
ins.close()

## for giving random value for every student
size=len(students)
rv = []
for i in range(0, size):
    rv.append(i)
#print(array[0].name)

for student in students:
    i = random.randint(0,size-1)
    tmp=rv[i]
    student.set_random(tmp)
    rv.remove(tmp)
    size -= 1

s_students=sorted(students, key=lambda student: (student.rank,student.random),reverse=True)
```

