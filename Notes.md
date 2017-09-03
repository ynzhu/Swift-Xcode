# Things you should know 

## 资源

由于 Playground 并没有使用沙盒机制，所以我们无法直接使用沙盒来存储资源文件。

但是，这并不意味着在 Playground 中没办法使用资源文件，Playground 提供了两个地方来存储资源，一个是每个 Playground 都独立的资源，而另一个是所有 Playground 都共享的资源。

### 独立资源

在打开的项目导航栏中可以看到有一个 Resources 目录，放置到此目录下的资源是每个 Playground 独立的。

这个目录的资源是直接放到 ```mainBundle``` 中的，可以使用如下代码来获取资源路径：
```
if let path = NSBundle.mainBundle().pathForResource("example", ofType: "json") {
    // do something with json
    // ...
}
```
如果是图片文件，也可以直接使用```UIImage(named:)```来获取。

### 共享资源

共享资源的目录是放在用户目录的 Documents 目录下的。在代码中可以直接使用
XCPlaygroundSharedDataDirectoryURL
来获取共享资源目录的 URL(需要先导入 ```XCPlayground``` 模块)。
```
import XCPlaygroud

let sharedFileURL = XCPlaygroundSharedDataDirectoryURL.URLByAppendingPathComponent("example.json")
```
注意：你需要创建~/Documents/Shared Playground Data目录，并将资源放到此目录下，才能在 Playground 中获取到

[请叫我小锅](http://www.jianshu.com/p/8b37c3ef645c)
