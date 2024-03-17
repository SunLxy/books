# IOS 开发

## react-native ios组件封装

### 引入本地framework

第一步:组件包的`react-native-demo.podspec`添加本地`framework`包引入

```podspec

# react-native-demo.podspec

require "json"

package = JSON.parse(File.read(File.join(__dir__, "package.json")))

Pod::Spec.new do |s|
  s.name         = "react-native-demo"
  s.version      = package["version"]
  # ...
  # 添加这个引入本地的 framework 包
  s.ios.vendored_frameworks = "ios/Frameworks/*.framework"
  
  # ...
end

```

第二步:在项目的`ios/Podfile`文件，手动添加`pod 'react-native-demo', :path => '../node_modules/react-native-demo'`

```podfile

# 项目中ios/Podfile文件

target 'example' do
  // .....
  pod 'react-native-demo', :path => '../node_modules/react-native-demo'

  // .....
  
end

```
