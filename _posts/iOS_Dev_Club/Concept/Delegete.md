title: "iOS delegete"
date: 2015-04-12 03:14:10
tags: [iOS concept,iOS delegete]
categories: [iOS,concept]
---

區塊B中的delegate回傳的數值，傳遞到區塊A的completionHandler
```
@property (copy, nonatomic) CBFetchPathResult tempCompletionHandler;

A:
if (.....) {
	self.tempCompletionHandler = completionHandler;
	[[WebDAVClient ....]];
}

B:
{
	if (self.tempCompletionHandler) {
		self.tempCompletionHandler(item, nil);
	}
}
```
[ref_fb][]

[ref_fb]:https://www.facebook.com/groups/iostw/permalink/883484025012281/