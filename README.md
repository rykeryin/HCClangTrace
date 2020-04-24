# HCClangTrace

## Installation

HCClangTrace is available through [CocoaPods](https://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'HCClangTrace'
```

## Usage
### 1. 在Build Settings中添加编译选项
Other C Flags增加`-fsanitize-coverage=func,trace-pc-guard`
如果你是OC Swift混编，则在Other Swift Flags增加`-sanitize-coverage=func`,`-sanitize=undefined`
### 2.统计程序启动的函数执行情况
在你的首页的viewDidAppear函数中加上生成orderFile的函数，然后运行app
```objc
- (void)viewDidAppear:(BOOL)animated {
    [super viewDidAppear:animated];
    [HCClangTrace generateOrderFile];
}

```
会在app的沙盒的tmp目录下生成，trace.order的文件
