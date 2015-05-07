title: "UIView Animations"
date: 2015-05-07 11:27:30
tags: []
categories: []
---
```
 [UIView beginAnimations:nil context:NULL];
    [UIView setAnimationDuration:0.3];
    [UIView setAnimationDelegate:self];
 
    //設定動畫開始時的狀態為目前畫面上的樣子
    [UIView setAnimationBeginsFromCurrentState:YES];
 
    textField.frame = CGRectMake(textField.frame.origin.x,
    textField.frame.origin.y - 210,
    textField.frame.size.width,
    textField.frame.size.height);
 
    [UIView commitAnimations];
```