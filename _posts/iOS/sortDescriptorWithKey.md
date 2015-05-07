title: "sortDescriptorWithKey"
date: 2015-05-07 11:27:30
tags: []
categories: []
---
```
 NSSortDescriptor *dateDescriptor = [NSSortDescriptor sortDescriptorWithKey:@"publish_date" ascending:NO];
 NSArray *sortDescriptors = [NSArray arrayWithObject:dateDescriptor];
 self.listData = [[self.listData sortedArrayUsingDescriptors:sortDescriptors] mutableCopy];
```