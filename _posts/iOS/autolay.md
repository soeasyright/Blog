title: "autolay"
date: 2015-05-07 11:27:30
tags: []
categories: []
---
```
//DEMO LOGO
UIImageView *demoLogo = [[UIImageView alloc]initWithImage:[UIImage imageNamed:@"DEMO LOGO.png"]];
[demoLogo setAlpha:0.88];
[self.view addSubview:demoLogo];
[demoLogo setTranslatesAutoresizingMaskIntoConstraints:NO];
 
//與superview的底部始終差距50個單位高度（不能小於）
NSLayoutConstraint *myConstraint;
myConstraint = [NSLayoutConstraint constraintWithItem:demoLogo attribute:NSLayoutAttributeBottom
                relatedBy:NSLayoutRelationGreaterThanOrEqual
                toItem:[demoLogo superview] attribute:NSLayoutAttributeBottom
                multiplier:1.0f constant:-50.0f];
[self.view addConstraint:myConstraint];
 
//x軸對齊superview的x軸中心點
myConstraint = [NSLayoutConstraint constraintWithItem:demoLogo attribute:NSLayoutAttributeCenterX
                relatedBy:NSLayoutRelationEqual
                toItem:[demoLogo superview] attribute:NSLayoutAttributeCenterX
                multiplier:1.0f constant:-0.0f];
[self.view addConstraint:myConstraint];
 
//寬度限制
myConstraint = [NSLayoutConstraint constraintWithItem:demoLogo attribute:NSLayoutAttributeWidth
                relatedBy:NSLayoutRelationEqual
                toItem:nil attribute:NSLayoutAttributeNotAnAttribute
                multiplier:1.0f constant:210.0f];
[self.view addConstraint:myConstraint];
 
//高度限制
myConstraint = [NSLayoutConstraint constraintWithItem:demoLogo attribute:NSLayoutAttributeHeight
                relatedBy:NSLayoutRelationEqual
                toItem:nil attribute:NSLayoutAttributeNotAnAttribute
                multiplier:1.0f constant:20.0f];
[self.view addConstraint:myConstraint];

```
```
UIView *ViewA = [[UIView alloc]init];
ViewA.backgroundColor = [UIColor orangeColor];
[ViewA setTranslatesAutoresizingMaskIntoConstraints:NO];
[self.view addSubview:ViewA];
 
UIView *ViewB = [[UIView alloc]init];
ViewB.backgroundColor = [UIColor blueColor];
[ViewB setTranslatesAutoresizingMaskIntoConstraints:NO];
[self.view  addSubview:ViewB];
 
 
NSMutableArray *myConstraints = [NSMutableArray array];
 
//從水平方向佈局
[myConstraints addObjectsFromArray:
    [NSLayoutConstraint constraintsWithVisualFormat:@"H:|-20-[ViewA(100)]-10-[ViewB(>=100)]-|"
        options:NSLayoutFormatDirectionLeadingToTrailing
        metrics:nil
        views:NSDictionaryOfVariableBindings(ViewA,ViewB)]];
 
 
//從垂直方向佈局
[myConstraints addObjectsFromArray:
    [NSLayoutConstraint constraintsWithVisualFormat:@"V:[ViewA(100)]-|"
        options:NSLayoutFormatDirectionLeadingToTrailing
        metrics:nil
        views:NSDictionaryOfVariableBindings(ViewA)]];
 
//從垂直方向佈局
[myConstraints addObjectsFromArray:
    [NSLayoutConstraint constraintsWithVisualFormat:@"V:[ViewB(ViewA)]-|"
        options:NSLayoutFormatDirectionLeadingToTrailing
        metrics:nil
        views:NSDictionaryOfVariableBindings(ViewB,ViewA)]];
 
[self.view addConstraints:myConstraints];

```
" V: " 和 " H: "
分別代表由垂直或是水平方向來佈局。
" | "
代表 Superview 的邊界。
" - "
代表預設寬度或高度，如果在中間加上數字 " -20- "，則代表限制 20 個單位高度或寬度。
" [ ] "
代表物件本身，括號內包含物件的變數名稱與大小限制，可以使用關係運算子（<＝、>＝ 或 ＝＝ 等）。
" @ "
優先權，1 至 1000 的整數，優先權較大的條件會優先被滿足，例如 ，[ViewB(>=100@1000)]，物件 ViewB 不可以小於 100 個單位長度或寬度會最優先被考慮。

```
//從水平方向佈局，由畫面左側開始，間距20個單位寬度，設定100單位寬度的ViewA，間隔10個單位寬度後，再設置單位寬度不能小於100的ViewB，最右側則與畫面間據一個預設距離
@"H:|-20-[ViewA(100)]-10-[ViewB(>=100)]-|"
 
//從垂直方向佈局，設定，ViewA為100個單位高度，並且與畫面底部間格一個預設距離
@"V:[ViewA(100)]-|"
 
//從垂直方向佈局，ViewB的高度與ViewA相同，並且與畫面底部間格一個預設距離
@"V:[ViewB(ViewA)]-|"
```