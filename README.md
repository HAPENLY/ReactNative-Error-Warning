**欢迎大家加群讨论**

点击链接加入群[ReactNative-解决问题交流群](https://jq.qq.com/?_wv=1027&k=4EZwdSd) :644124441

点击链接加入群[ReactNative技术交流群2](https://jq.qq.com/?_wv=1027&k=55Dujm4)  :687663534

# ReactNative-Error-Warning
注：本文是我在开发过程中遇到问题[{持续更新看过来}解决方法的总结](http://www.jianshu.com/p/98c8f2a970eb)，之后会持续更新，希望帮助到更多的学习者。文中有不妥的地方希望指出共同学习，同时欢迎大神补充。（之后我会放出自己开发整理的笔记和demo）欢迎持续喜欢关注。

## 错误1：

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-aeaa75c85658db5e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
估计是程序中有格式错误请自行检查比如：你注释出来问题。

`{/*title="张三"*/}`换`//title="张三"`

## 错误2：

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-5d363498f41d96ca.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这个说明你要跳转的页面缺少子控件。所以你要在里面添加东西比如加个：`<View></View>`

## 警告3：调试警告

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-5d06ced8033b2908.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

看下报的警告就知道调试程序在这个窗口导致运行缓慢，所以建议你换一个单独新的窗口进行调试

## 警告4：

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-193cb2e2678e3a63.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
[解决方法就是你的Xcode没有适配HTTPS iOS9的](http://stackoverflow.com/questions/38077273/react-native-fetch-network-request-failed-not-using-localhost)
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-33e5987eba518031.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
加上：
```
 <key>NSAppTransportSecurity</key>
 <dict>
  <key>NSAllowsArbitraryLoads</key>
  <true/>
 </dict>
```
## 错误4：

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-2e0f228bb0de7a8f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这个很神奇。遇到了不要紧张多按 ⌘R几下或者把模拟器上的项目删除之后重新加载一般就会解决

## 错误5：


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-ed25a5c50563288a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

认真看下错误信息，上面说你忘记返回值了 所以你的函数中少了一个return（）；

## 错误6:

![](http://upload-images.jianshu.io/upload_images/436736-2a43c135e9b8cd09.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如果你检查代码确实没有错误。还报这个错，那就说明你的端口被占用了。打开终端，切换到项目目录。执行react-native start
如果出现`Packager can't listen on port 8081`那说明端口被占用了。

：根据命令行提示进行操作：

1.`lsof -n -i4TCP:8081 `   列出被占用的端口列表
2.`kill -9 <PID>`    找到与之对应的PID然后删除即可

## 错误7：

```
SyntaxError: SyntaxError /Users/zhaopengsong/Desktop/ReactNative/BuyDemo/Component/Main/ZPMain.js: JSX value should be either an expression or a quoted JSX text (107:22)
```

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-813059f0bda53166.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


语法错误，JSX语法必须用{}对变量进行赋值：如`title=titleName`换为`title={titleName}`
或者检查下有没有其他的语法错误，比如少了`逗号`多了`分号`这些低级错误

## 错误8

```
Requiring unknown module "undefined".If you are sure the module is there, try restarting the packager or running "npm install"
```

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-c18216dc04cc7f13.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


这个错误我的解决思路是：之前改过什么，撤回，一般是用到了错误的react-native 方法导致的。


## 错误9：

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-e42a88e6226daafc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

原因：没有启动后台react-Native 服务。即终端

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-68cba2a4482ffc0b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 错误10：

如果你遇到了列如九宫格不自动换行的情况，检查一下样式里面有没有这两句话`flex-start：交叉轴的起点对齐。``wrap：换行，第一行在上方。`

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-f11b892ccfddffc6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 错误11：

```
ExceptionsManager.js:63 Expected a component class, got [object Object]
```

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-27ec35b43e788a2d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

解决方法：

You need to rename your `commonView`class to   `CommonView`, the class must be **capitalize**


## 错误12：

![NSURLErrorDomain](http://upload-images.jianshu.io/upload_images/436736-a81b9dc41f134124.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这是你请求的URL错误。要是`https://` 的才行。

##错误 13：
** 创建新项目，react-native init 项目名命令长时间无响应，或报错shasum check failed **

react-native命令行从npm官方源拖代码时会遇上麻烦。请将npm仓库源替换为国内镜像：

```
npm config set registry https://registry.npm.taobao.org --global 
npm config set disturl https://npm.taobao.org/dist --global
```

另，执行init时切记不要在前面加上sudo

## 错误14：
** 修改8081默认端口号的两种方式 **

（1）启动项目时react-native start --port 8083
（2）手动修改项目下的node_modules\react-native\local-cli\server\server.js下的方法server.js文件，如下图所示。

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-fc59bf9b481d474e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 错误15：

```
Application NewsDemo has not been registered. 
This is either due to a require() error during initialization 
or 
failure to call AppRegistry.registerComponent.
```

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-82b362e389e2cf25.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

错误原因是端口冲突。解决方法是看** 错误14 **

其次解决方法是：

```
1、终端
2、cd 到项目目录
3、react-native start
4、lsof -n -i4TCP:8081 //这句可以看打印出8081端口下的服务
5、kill -9 <PID>    //终止你其他占用端口
```
如图：

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-1bed605cfe7fc1c5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 错误16：

 如果你遇到了这个问题，并解决了。希望能在下面留言帮助更多的人。感谢！(我的错误原因是require路径出错，我是换用URI 加载image资源解决的)
 
![](http://upload-images.jianshu.io/upload_images/436736-f94e8a164a925216.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 错误17：

错误出现执行`react-native run-ios`出现下面错误
 
```
Failed to install the requested application
An application bundle was not found at the provided path.
Provide a valid path to the desired application bundle.
Print: Entry, ":CFBundleIdentifier", Does Not Exist

Command failed: /usr/libexec/PlistBuddy -c Print:CFBundleIdentifier build/Build/Products/Debug-iphonesimulator/ReactNativexx.app/Info.plist
Print: Entry, ":CFBundleIdentifier", Does Not Exist
```

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-a84af4bced0eeef6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


[解决方法:](http://stackoverflow.com/questions/35243601/react-native-build-commands-failed-phasescriptexecution-domain-nsposixerro)

1、尝试reset一下 模拟器之后再`react-native run-ios`
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-32b0be0c88bed5ec.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2、尝试执行`react-native upgrade`  然后一路enter  
     再`react-native run-ios`试试？
     
## 错误18：


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-10f420619f077a3d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


解决：

```
var View = React.View;

/* later... */
propTypes: {
    ...View.propTypes,
    myProp: PropTypes.string
}
```

## 错误19：
(这个错误我的解决方法是新建项目，把组件放到新项目，重新安装第三方，然后`run`,虽然笨了点，但是问题解决了。)

啊。。。。。这个问题让我头痛死了[来看看GitHub上的讨论]

哪位大神知道便捷的解决方案希望评论给出！感激！

(https://github.com/facebook/react-native/issues/4968)

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-0792bb843c1613ff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


尝试解决：
1、`react-native link` ||`rnpm link`一下然后再安装
`react-native run-ios `遇到：


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-a98328772ea11361.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 错误20：

Application textDemo has not been registered. This is either due to a require() error during initialization or failure to call AppRegistry.registerComponent.

![14C430A5-CA91-4731-89E0-55318AB9AACF.png](http://upload-images.jianshu.io/upload_images/436736-8ce104c881881225.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

解决方案：

1、是注册的时候写错了。也就是这段话注册的不对：
AppRegistry.registerComponent('textDemo', () => textDemo);
注意：‘textDemo’这个是项目名 textDemo这个你可以随自己你喜好指定。
 
2、很有可能是8081端口被占用了
你可以尝试：切换到项目所在目录，输入`react-native start `如果出现`Packager can't listen on port 8081`那说明端口被占用了。
根据命令行提示进行操作：
1.`lsof -n -i4TCP:8081`    列出被占用的端口列表
2.`kill -9 <PID>  `  找到与之对应的PID然后删除即可

3.重新运行项目 react-native run-ios/android

## 错误21 ：

如果你项目中频繁遇到：
'RCTRootView.h'file  not found.
RCTBridgeModule.h file not found


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-4f39bbabb3badfa9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


解决方法：
1、添加link  ：`$(SRCROOT)/../node_modules/react-native/React`
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-3da958b9e5b71419.png)
2、到项目目录下` sudo npm install`试试。
3、 
```
#import "RCTBridgeModule.h"
换为

#import <React/RCTBridgeModule.h>
```

## 警告22⚠️：

安装的过程中可能会遇到UNMET PEER DEPENDENCY的错误 

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-08710ada020c9565.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

解决办法就是在安装的时候 指定具体的版本安装：`sudo npm install -g react@~15.4.1`
这个警告：	

npm WARN react-native@0.42.3 requires a peer of react@15.4.1 but none was installed.

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-2d8034612fa23681.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

解决：

`npm install –save react@15.4.1`

## 警告23⚠️：屏蔽OS_ACTIVITY_MODE.log

react-native  运行应用xcode打印log`__nw_connection_get_connected_socket_block_invoke Connection has no connected handler`
解决方法：

```
1. Xcode menu -> Product -> Edit Scheme...
2. Environment Variables -> Add -> Name: "OS_ACTIVITY_MODE", Value:"disable"
3. Run your app again, done! 这样就没问题了
```
图示：

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-38105c4f52db6292.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-70f66ec08fc1385b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-888e593bccb31c40.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-cb3c8a2533de7f86.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 错误24：

```
Unable to resolve module `react/lib/ReactComponentWithPureRenderMixin` from
`/Users/song/Desktop/ReactNativeRouterFlux/node_module
s/react-native-experimental-navigation/node_modules/react-addons-pure-render-mixin/index.js`:
 Module does not exist in the module map or in these directories:
```

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-4723b21ed6bb5431.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/436736-683f360d9d20cbe1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

解决：
类似这种错误，就是缺少模块，通过npm i react-addons-pure-render-mixin -S 命令即可，标记部分是你缺少的模块名。
如果这样解决不了问题，那你需要降低的的RN版本。可能版本过新了。
1、查看你的版本：` react-native --version`
2、安装适当的版本：`npm install --save react-native@0.42.3`
3、更新一下模板：`react-native upgrade`

## 错误25

```
RCTSRWebSocket.m报错
Ignoring return value of function declared with warn_unused_result attribute
```

这个报错在此文件中有两处，代码

`SecRandomCopyBytes(kSecRandomDefault, sizeof(uint32_t), (uint8_t *)mask_key);`
修改为
`(void)SecRandomCopyBytes(kSecRandomDefault, sizeof(uint32_t), (uint8_t *)mask_key);`
前面加上`(void)`。

```
RCTScrollView.m 报错
Use of undeclared identifier '_refreshControl'; did you mean 'refreshControl'?
```
解决：

```
@implementation RCTCustomScrollView
{
  __weak UIView *_dockedHeaderView;
  RCTRefreshControl *_refreshControl;  // 加入此行
}
```

## 警告26⚠️：

```
[ReactJS Warning: Each child in an array or iterator should have a unique “key” prop]
```

![image.png](http://upload-images.jianshu.io/upload_images/436736-a7a430b4cb6d622c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

遇到这个警告说明你的多个视图数组需要给个KEY标示！
可以给每个控件加上Key这样写:

```
<Text  key={0} style={{ position:'absolute', width:imgwidth,height:imgheight,top:64+Y,left:X,fontSize:parseInt(layoutData.fontsize)}}>{texts}</Text>
 ```
