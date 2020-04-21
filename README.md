**欢迎大家加群讨论**


![image.png](https://upload-images.jianshu.io/upload_images/436736-48e6e32fecc2095d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# ReactNative-Error-Warning
注：本文是我在开发过程中遇到问题[解决方法的总结](https://github.com/HAPENLY/ReactNative-Error-Warning)，之后会持续更新，希望帮助到更多的学习者。文中有不妥的地方希望指出共同学习，同时欢迎大神补充。（之后我会放出自己开发整理的笔记和[GithubDemo地址,欢迎 star](https://github.com/HAPENLY/ReactNative-Source-code-Demo)）欢迎持续喜欢关注 star。  
遇到问题的可以来这个群里交流: `1085660877 ` 欢迎对 ReactNative 开发感兴趣的朋友加入!   1085660877

这是第二次发，之前的文章被消失了

**欢迎大家加群讨论**

点击链接加入群[ReactNative-解决问题交流群](https://jq.qq.com/?_wv=1027&k=4EZwdSd) :644124441

点击链接加入群[ReactNative技术交流群2](https://jq.qq.com/?_wv=1027&k=55Dujm4)  :687663534

[点击链接加入群聊【ReactNative技术交流群3】：](https://jq.qq.com/?_wv=1027&k=5ziQ7I1)1085660877

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

## 错误 27：Warning: Failed prop type: Invalid prop `source` supplied to `RCTImageView`  OR
ExceptionsManager.js:71 Warning: Failed prop type: Invalid prop `source` supplied to `Image`.

![image.png](http://upload-images.jianshu.io/upload_images/436736-e5cfe81503eafb04.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

解决：这个错误的原因是你给Image 的Source 有问题 比如不是一个URI ，查看一下不是不传入了一个对象像这样。
![image.png](http://upload-images.jianshu.io/upload_images/436736-8320dd9e428ca7e8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
## 错误28：
```
RN iOS 0.45以上版本开始需要依赖一些第三方编译库，这些库在国内下载都非常困难（一般的翻墙工具都很难下载）未来RN不同版本可能依赖不同版本的第三方编译库，具体所需库和版本请查看[ios-install-third-party.sh](https://github.com/facebook/react-native/blob/master/scripts/ios-install-third-party.sh)文件，注意先把左上角的branch切换到对应的版本
boost/iterator/iterator_adaptor.hpp' file not found
```
[解决参考](http://reactnative.cn/blog.html)

## 错误29 Android 项目启动报这个错误:`Could not connect to development server`
首先检查包服务器是否运行正常。
       在项目文件夹下输入react-native start或者npm start均可开启服务器，但是我们需要在PC端确认包服务器是否运行正常。
![image.png](http://upload-images.jianshu.io/upload_images/436736-1e2e20e8b0deea60.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

解决: 1.手机摇一摇进入到Developer Menu  如图:
![5E8F32EC-5199-4140-A1B8-826E2A206DBA.png](http://upload-images.jianshu.io/upload_images/436736-b50d77e64a4f7e21.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2.选择 Dev Settings 如图:

![image.png](http://upload-images.jianshu.io/upload_images/436736-dc0ac760f1be0212.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
3.填写 你的服务 IP 记得端口为:8081
![image.png](http://upload-images.jianshu.io/upload_images/436736-bcc7fc453ed9ac6b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
4.点击确定之后重新启动项目, reload 搞定

## 30 错误
```
TransformError: /Users/xxxxt/index.ios.js: Unexpected token ) (While processing preset: \"/Users/xxx/node_modules/babel-preset-react-native/index.js\")"
```

![image.png](http://upload-images.jianshu.io/upload_images/436736-f023ed5d0ee9d109.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

解决方法:
```
yarn remove babel-preset-react-native
yarn add babel-preset-react-native@2.1.0
```
## 31 `unrecognized font family material icons`

解决方法:
1.Close the running packager
2.Run `react-native link react-native-vector-icons`
3.Then run `react-native start --reset-cache`
4.Finally run `react-native run-ios` to restart the simulator

## 32 
`undefined is not an object (evaluating NativeModuels.UIManager.RCTVideo.Constants')
`
![image.png](http://upload-images.jianshu.io/upload_images/436736-e9720f2cc714794b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
依次执行:
 1.`npm i -S react-native-video`
2.`react-native link `
3.`然后重启模拟器试(也可以把应用从模拟器删除clean 之后重新 run)试我是这样好的`
[可参考issues](https://github.com/react-native-community/react-native-video/issues/272)
## 33 如果uninstall 第三方库之后然后 install xcode 报错`linker command failed with exit code 1 (use -v to see invocation) `
解决方法:


![image.png](http://upload-images.jianshu.io/upload_images/436736-505d451ba08654f0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


```
1.别慌
2.检查一下是不是 install 的时候没有删除module 直接 install 导致的多了或者少了.a文件,我的是这样解决的.
```
## 34 `underfined is not an object(evaluating 'viewproptypes.style')`

![image.png](http://upload-images.jianshu.io/upload_images/436736-5104a80293cc9317.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

解决方法:一.
```
https://github.com/facebook/react-native/issues/14032
看完之后，解决了问题。
解决方式如下：
找到node_modules目录下的react-native-scrollable-tab-view，将所有js文件中有
ViewPropTypes.style 改为 View.propTypes.style
```
解决方法二.对于旧项目 三方库较多不好修改
```
就是新建一个项目,然后把组件放到新项目中.重新 yarn add 一下你所有的库.  
如果你只改 RN 版本可能会有其他组件版本跟不上.这样就确保都是最新的版本了
这个方法我已经验证过可以的
```
## 35 : 旧项目升级到RN 0.47.1 + 之后出现这个问题
```
Navigator is deprecated and has been removed from this package. It can now be installed ' +
'and imported from `react-native-deprecated-custom-components` instead of `react-native`. ' +
'Learn about alternative navigation solutions at http://facebook.github.io/react-native/docs/navigation.html'
```
![image.png](http://upload-images.jianshu.io/upload_images/436736-e2439d8115e52904.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
解决:
1.根据提示:
![image.png](http://upload-images.jianshu.io/upload_images/436736-bb3a4107684f0c26.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2.找到对应` JS `文件找到并删除:
![image.png](http://upload-images.jianshu.io/upload_images/436736-70a70f41196b81c2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
3.添加:`import {Navigator} from 'react-native-deprecated-custom-components'`
4安装 `yarn add react-native-deprecated-custom-components`
5.run 就搞定了

## 36: props的使用以及propTypes填坑`undefined is not an object (evaluating '_react2.PropTypes.string')`(群友:@Dennis  [提供参考连接](http://www.mamicode.com/info-detail-2017422.html)) 错误详情如图:![image.png](http://upload-images.jianshu.io/upload_images/436736-134dac724d3bbe76.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/436736-ced41c1af3707a76.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 37 : `No bundle URL present.`

![image.png](http://upload-images.jianshu.io/upload_images/436736-95462223b530d595.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
解决方法:
首先:
```
npm install
react-native run-ios
```
然后看看你是否开着`Shadowsocks,VPN `之类的.关掉重新 `Run` 试试 
![image.png](http://upload-images.jianshu.io/upload_images/436736-a0d3a672e4b766dc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 38:` Redefinition of 'RCTMethodInfo'`
![image.png](http://upload-images.jianshu.io/upload_images/436736-84e3d7246a76be14.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
如果你使用的是最新的 RN 版本.建议切换为目前相对稳点的0.47.2版本
[解决方案参考 issues](https://github.com/facebook/react-native/issues/15775)
[解决方案参考 issues](https://github.com/facebook/react-native/issues/15762)

## 39 react-native 低版本升级到0.49以上版本时遇到
```
Script-00DD1BFF1BD5951E006B06BC.sh: line 3: ../node_modules/react-native/packager/react-native-xcode.sh: No such file or directory
```
解决方法:
1.打开 `Xcode Build Phases > Bundle React Native code and images`
2修改`export NODE_BINARY=node
../node_modules/react-native/packager/react-native-xcode.sh` 为` export NODE_BINARY=node
../node_modules/react-native/scripts/react-native-xcode.sh`

## 40 当使用 State 报错
`undefined is not an object evaluating this.state.`
![image.png](http://upload-images.jianshu.io/upload_images/436736-ca5eb06bb3e61509.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
方法一:
在方法调用的时候添加`.bind(this)` 如![image.png](http://upload-images.jianshu.io/upload_images/436736-cc40670940900b69.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
方法二:在构造函数中添加绑定
![image.png](http://upload-images.jianshu.io/upload_images/436736-76052805147af881.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
方法三: 或者使用箭头函数.`()=>{}`
方法有很常用的这几种

## 41 如果你频繁出现这个错误,
 `nvariant Violation: Element type is invalid: expected a string (for built-in components) or a class/function (for composite components) but got: object.
`
同时出现这个警告:` Can only update a mounted or mounting component. This usually means you called setState, replaceState, or forceUpdate on an unmounted component. This is a no-op.
`  
![image.png](http://upload-images.jianshu.io/upload_images/436736-1a7fd004e809af7f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

解决方法:
一.是查看导入的工具类是否
`var xxxx = require('../Utils/ZPxxxx'); `这样加入的, 如果是你那就傻逼了改成这样试试` import xxxx from '../Utils/ZPxxxx';`  
同时警告是因为:你在一个被卸载的组件里调用setState方法.检查一下生命周期一般没啥影响

感谢群友@勿念  丫头 提醒我这里在详细解释一下
导出单个类:
```
在ES5里，要导出一个类给别的模块用，一般通过module.exports来导出

//ES5
var ZPxxxx = React.createClass({
    ...
});
module.exports = ZPxxxx;
在ES6里，通常用export default来实现相同的功能：

//ES6
export default class ZPxxxx extends React.Component{
    ...
}
引用的时候也类似：

//ES5
var ZPxxxx = require('./ZPxxxx.js');

//ES6
import ZPxxxx from './ZPxxxx.js';

```
## 42 如果你在跳转页面的时候经常遇到`undefined is not an object (evaluating 'this.props.navigation.navigate')`  
![image.png](http://upload-images.jianshu.io/upload_images/436736-2056d93ac3d77180.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
解决方法见 [GitHub issues](https://github.com/react-navigation/react-navigation/issues/1569) 这里面有详细的解释和介绍@matthamil解释很到位!
react-Navigation使用详解:
[Screen-Navigation-Prop](https://reactnavigation.org/docs/navigators/navigation-prop#Screen-Navigation-Prop)

## 43项目 Run的时候经常报:` Failed to load bundle(http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false) with error:(Could not connect to development server.  Ensure the following: - Node server is running and available on the same network - run 'npm start' from react-native root - Node server URL is correctly set in AppDelegate - WiFi is enabled and connected to the same network as the Node Server`  
解决方法
1: 启动项目的服务:`react-native start   `或者`npm start`;然后早 `Com+R`;
2:上面的方法没有解决,而且长时间不能启动还报以上错误: 
在 `xcode ->build phases -> bundle react-native code and image `->添加
`export DISABLE_XIP=NOTHANKS`或者:`export DISABLE_XIP=true`
![image.png](http://upload-images.jianshu.io/upload_images/436736-97476f7b0a9fbfe8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
原因详细介绍见 [GitHub issue](https://github.com/facebook/react-native/issues/12786) 

解决方法二: `sudo react-native start  ` 输入密码 `run`  
========================================================

## 44 优化打包速度(真机运行速度)
#### 原因
就是`react-native-xcode.sh`. 每次打包安装都重新把RN文件打包成`main.jsbundle`, 在机械硬盘的渣渣电脑上操作那数以万计个的文件,所以会很慢
####解决:
找到:![image.png](https://upload-images.jianshu.io/upload_images/436736-0279b9a9a838e463.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
这个脚本`react-native-xcode.sh`在最头上加上
```
if [ "$CONFIGURATION" = "Debug" ]; then
  echo "--- Skip bundle building in 'Debug' mode"
  exit 0
fi
```
或者:
```
DEST=$CONFIGURATION_BUILD_DIR/$UNLOCALIZED_RESOURCES_FOLDER_PATH

if [ "$CONFIGURATION" = "Debug" ] && [ -f "$DEST/main.jsbundle" ]; then
  echo "--- Skip bundle building in 'Debug' mode"
  exit 0
fi
```
这样真机测试的手安装就会快了.
#####注意 :如果你是打包需要注意修改代码后
,需要Command+Shift+K清除工程缓存, 重新Build, 生成新的main.jsbundle.

## 45 如果你执行 `react-native init AwesomeProject ` 报错
```
info No lockfile found.
[1/4] 🔍  Resolving packages...
warning react-native > fbjs-scripts > gulp-util@3.0.8: gulp-util is deprecated - replace it, following the guidelines at https://medium.com/gulpjs/gulp-util-ca3b1f9f9ac5
error An unexpected error occurred: "Couldn't find package \"esutils@^2.0.2\" required by \"babel-code-frame@^6.26.0\" on the \"npm\" registry.".
...
...
 stderr: null,
  stdout: null,
  pid: 26012,
  output: [ null, null, null ],
  signal: null,
  status: 1 }
Command `yarn add react-native --exact` failed.

```
解决方法: `npm config set registry https://registry.npmjs.org` 
如果下载过慢就用这个`npm config set registry https://registry.npm.taobao.org`

## 46 警告 使用 sectionlist 遇到
 ```
 Warning: Failed child context type: Invalid child context `virtualizedCell.cellKey` of type `number` supplied to `CellRenderer`, expected `string`.
```
![image.png](https://upload-images.jianshu.io/upload_images/436736-f1c3744301c62add.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

消除方法:`keyExtractor={(item, index) => index.toString()}`
##47 Android 项目 run 遇到 `React Native Version Mismatch`
Javascript version 0.54.4和 native 0.55.4 版本不一致   :
解决方法如下：

进入：android/app/build.gradle文件，找到dependencies代码块，添加 这里要和你 Javascript 版本一致
```
dependencies {
    compile ("com.facebook.react:react-native:0.54.4") { force = true } 
}
```
## 48 项目运行遇到:
 `No component found for view with name "ARTShape"`
` No component found for view with name "ARTSurfaceView"`

解决方法是:
1).xcode中打开ios项目，选中‘Libraries’目录—> 右键选择‘Add Files to 项目名称’ —> ‘node_modules/react-native/Libraries/ART/ART.xcodeproj’ 添加；
2).选中项目根目录 —> 点击’Build Phases‘ —> 点击‘Link Binary With Libraries’ —> 点击左下方‘+’ —> 选中‘libART.a’添加。

## 49 如果真机运行出现
`Showing All Messages
error: File xx/BuildProductsPath/Release-iphoneos/xx/main.jsbundle does not exist. This must be a bug with`

解决方法:(建一个就好了)
`sudo react-native bundle --entry-file index.js --bundle-output ./ios/main.jsbundle --platform ios --assets-dest ./ios --dev false`
