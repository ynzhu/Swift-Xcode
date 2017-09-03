# Things you should know 
## Sources 目录

通常情况下，我们直接在 Playground 上面写代码，然后编译器会实时编译我们代码，并将结果显示出来。这很好，我们可以实时得到代码的反馈。

但是这也会产生一个问题，如果我们写了一个函数，或者自定义了一个 view，这部分代码一般情况下是不会变的，而编译器却会一次又一次地去编译这些代码，最终的结果就是导致效率的低下。

这时，Sources 目录就派上用场了，使用 Cmd + 1 打开项目导航栏(Project Navigator)，可以看到一个 Sources 目录。放到此目录下的源文件会被编译成模块(module)并自动导入到 Playground 中，并且这个编译只会进行一次(或者我们对该目录下的文件进行修改的时候)，而非每次你敲入一个字母的时候就编译一次。 这将会大大提高代码执行的效率。

```注意：由于此目录下的文件都是被编译成模块导入的，只有被设置成 public 的类型，属性或方法才能在 Playground 中使用。```

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

From [请叫我小锅](http://www.jianshu.com/p/8b37c3ef645c)
