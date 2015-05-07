title: "UIViewResize"
date: 2015-05-07 11:27:30
tags: []
categories: []
---
```
//原始影像
UIImage *image =[UIImage imageNamed:@"Original.png"];
 
//製作一個ImageContext並符合新的大小設定
UIGraphicsBeginImageContext(CGSizeMake(200, 200));
 
//將原始影像重繪在此範圍中
[image drawInRect:CGRectMake(0, 0, 200, 200)];
 
//以目前的ImageContext來製作新的UIImage
UIImage *resizeImage =UIGraphicsGetImageFromCurrentImageContext();
UIGraphicsEndImageContext();
- See more at: http://furnacedigital.blogspot.tw/2012/08/uiimage.html#more


//透過size屬性
CGFloat w, h;
w = image.size.width;
h = image.size.height;
- See more at: http://furnacedigital.blogspot.tw/2012/08/uiimage.html#more


//在CGImageRef型態下取得大小
CGFloat w, h;
CGImageRef imageRef = image.CGImage;
w = CGImageGetHeight(imageRef);
h = CGImageGetWidth(imageRef);
- See more at: http://furnacedigital.blogspot.tw/2012/08/uiimage.html#more
```