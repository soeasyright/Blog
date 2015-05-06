title: "sgque"
date: 2015-04-12 01:17:33
tags: []
categories: []
---
https://www.facebook.com/groups/iostw/permalink/948649875162362/

- (void)prepareForSegue:(UIStoryboardSegue *)segue sender:(id)sender {
.....

segue.sourceViewController ///< 來源 vc
segue.destinationViewController ///< 要去的vc
}

這個segue 要不要被執行可以用

- (BOOL)shouldPerformSegueWithIdentifier:(NSString *)identifier sender:(id)sender {
.....
}
來決定