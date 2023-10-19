# LightWebView
LightWebView是一款使用Android原生开发的Unity Android环境下的轻量WebView插件,Unity Android工程通过集成它可以轻松的获取打开url(打开新的Activity)的能力.
### 1. 插件构成
+ LightWebview/Plugins/Android  插件核心文件
  + lightwebviewsdk-release.aar  Android 原生 WebView SDK.
  + lightwebviewunity-release.aar  lightwebviewsdk的Unity Api.
  + LightWebviewAndroid.cs C#脚本.

### 2. 集成方式
+ 引入 LightWebView_1.0.0.unitypackage
   
+ 配置依赖
  + 在 Project Settings-Player-Publishing Settings-Build 中勾选 Custom Main Gradle Template 和 Custom Gradle Properties Template 后,会在Assets/Plugins/Android目录下生成 gradleTemplate.properties 和 mainTemplate.gradle.
  + 在 mainTemplate.gradle 文件的dependencies代码块中添加以下依赖项:
    ```java
    implementation 'androidx.appcompat:appcompat:1.3.0'
	implementation 'com.google.android.material:material:1.4.0'
	implementation 'androidx.constraintlayout:constraintlayout:2.0.4'
    ```
+ 使用插件
   ```c#
   //打开url不指定后退模式,等同于传入LightWebviewAndroid.CloseMode.close
   LightWebviewAndroid.instance.open(url);

   //打开url并指定后退模式
   //LightWebviewAndroid.CloseMode.back: 返回键执行网页的后退方法
   //LightWebviewAndroid.CloseMode.close: 返回键执行关闭方法
   LightWebviewAndroid.instance.open("https://aios.soinluck.com/scene?sk=q842c2e079a1b32c8", LightWebviewAndroid.CloseMode.back);
   ```
  
