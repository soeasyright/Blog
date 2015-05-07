title: "MPMoviePlayerController"
date: 2015-05-07 11:27:30
tags: []
categories: []
---
```
//設定影片檔路徑
NSString *path = [[NSBundle mainBundle] pathForResource:@"Furnace" ofType:@"m4v"];
NSURL *url = [NSURL fileURLWithPath:path];
 
//player為MPMoviePlayerController型態的指標
player = [[MPMoviePlayerController alloc] initWithContentURL:url];
 
//旋轉90度
player.view.transform = CGAffineTransformMakeRotation(1.5707964);
 
//使用Observer製作完成播放時要執行的動作
[[NSNotificationCenter defaultCenter] addObserver:self
                                      selector:@selector(moviePlayBackDidFinish:)
                                      name:MPMoviePlayerPlaybackDidFinishNotification
                                      object:player];
 
//設定影片比例的縮放、重複、控制列等參數
player.scalingMode = MPMovieScalingModeAspectFit;
player.repeatMode = MPMovieRepeatModeNone;
player.controlStyle = MPMovieControlStyleDefault;
 
//將影片加至主畫面上
player.view.frame = self.view.bounds;
[self.view addSubview:player.view];
 
[player play];

```
```
//自動縮放符合畫面比例
player.view.autoresizingMask = UIViewAutoresizingFlexibleWidth|UIViewAutoresizingFlexibleHeight;

//將專案內此函式的註解拿掉並回傳YES
- (BOOL)shouldAutorotateToInterfaceOrientation:(UIInterfaceOrientation)interfaceOrientation {
    //啟用畫面自動旋轉
    return YES;
}
```
```
//自行定義影片播放完成的函式
- (void)moviePlayBackDidFinish:(NSNotification *)notification {
 
    //因為只播放一次所以在這就直接移除此Observer
    [[NSNotificationCenter defaultCenter] removeObserver:self
                                          name:MPMoviePlayerPlaybackDidFinishNotification
                                          object:player];
    [player stop];
 
    //將影片重畫面上移除
    [player.view removeFromSuperview];
    [player release];
}
```
http://furnacedigital.blogspot.tw/2011/02/mpmovieplayercontroller.html