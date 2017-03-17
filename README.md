# SLSlideMenu
一句代码上/下/左/右弹出菜单
## 效果图
![SLSlideMenu](http://upload-images.jianshu.io/upload_images/1733477-d67eb45b36d64eee.gif?imageMogr2/auto-orient/strip) 
    
## 使用说明

### 安装

    将SLSlideMenu文件夹拖入项目
    
### 调用

```Objective-C
1> #import "SLSlideMenu.h"
2> [SLSlideMenu slideMenuWithFrame:CGRectMake(0, 64, screenW, screenH) delegate:self direction:SLSlideMenuDirectionLeft       slideOffset:400 allowSwipeCloseMenu:YES aboveNav:NO];
   或者在viewdidload中：
   [SLSlideMenu prepareSlideMenuWithFrame:self.view.frame delegate:self direction:SLSlideMenuSwipeDirectionLeft slideOffset:300 allowSlideMenuSwipeShow:YES allowSwipeCloseMenu:YES aboveNav:YES];
```

### 自定义menu控件：

```Objective-C
1> 遵守协议<SLSlideMenuProtocol>
2> 实现代理方法：将子控件添加到menuView
 - (void)slideMenu:(SLSlideMenu *)slideMenu prepareSubviewsForMenuView:(UIView *)menuView {
    UILabel *lb = [[UILabel alloc] initWithFrame:CGRectMake(20, 50, 100, 30)];
    lb.text = @"自定义控件";
    lb.font = [UIFont systemFontOfSize:12];
    lb.textColor = [UIColor darkGrayColor];
    [menuView addSubview:lb];
 }
```   
    
    
## 接口说明
      
####  点击弹出的场景

```Objective-C
/**
* 配置menu视图。可在viewdidload中，此种方式可通过左滑右滑手势呼出。
*param frame 如果不要盖住nav 就传self.view.frame；如果要盖住nav就传CGRectMake(0, 64, screenW, screenH)
*param delegate 代理 可通过设置代理来配置menu的子控件
*param direction 手势滑出方位。SLSlideMenuSwipeDirectionRight代表从右边滑出
*param slideOffset menu的宽度/高度
*param allowSlideMenuSwipeShow 是否允许手势滑出
*param allowSwipeCloseMenu 是否允许手势关闭
*param aboveNav 是否盖住nav
*param identifier 标识符 可以通过设置进行唯一标识
*/
+ (void)prepareSlideMenuWithFrame:(CGRect)frame delegate:(id <SLSlideMenuProtocol> )delegate direction:(SLSlideMenuSwipeDirection)direction slideOffset:(CGFloat)slideOffset allowSlideMenuSwipeShow:(BOOL)isAllowSwipeShow allowSwipeCloseMenu:(BOOL)isAllowSwipeCloseMenu aboveNav:(BOOL)isAbove identifier:(NSString *)identifier;
```

####  手势滑出的场景

```Objective-C
/**
* 创建menu视图。此方式一般用在点击弹出的场景，不支持手势滑出。
*param frame 如果不要盖住nav 就传self.view.frame；如果要盖住nav就传CGRectMake(0, 64, screenW, screenH)
*param delegate 代理 可通过设置代理来配置menu的子控件
*param direction menu弹出方位。SLSlideMenuSwipeDirectionRight代表从右边弹出
*param slideOffset menu的宽度/高度
*param allowSwipeCloseMenu 是否允许手势关闭
*param aboveNav 是否盖住nav
*param identifier 标识符 可以通过设置进行唯一标识
*/
+ (void)slideMenuWithFrame:(CGRect)frame delegate:(id <SLSlideMenuProtocol> )delegate direction:(SLSlideMenuDirection)direction slideOffset:(CGFloat)slideOffset allowSwipeCloseMenu:(BOOL)isAllow aboveNav:(BOOL)isAbove identifier:(NSString * )identifier;
```
