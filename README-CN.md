
## 目录
1. 在可玩广告平台申请应用ID及广告位ID
2. 添加MoPub SDK和PlayableAds SDK
3. 将以下文件添加到工程里面 
4. 在MoPub平台为可玩广告配置广告位 
5. 在MoPub平台增加可玩广告为新的广告源 
6. 在MoPub平台打开可玩广告广告源 
7. 确认可玩广告配置成功 
8. 在工程中使用MoPub请求可玩广告 
9. 调试
10. 示例

---

## 1. 在可玩广告平台申请应用ID及广告位ID
#### 1.1 进入“应用管理”页面，点击添加“添加应用”按钮
![“应用管理”页面](imgs/001.png)

#### 1.2 填写相关信息，点击“添加”按钮，返回应用管理列表页 
![添加](imgs/002.png)

#### 1.3 在应用管理列表页，获取应用的ID
![应用管理列表页](imgs/003.png)

#### 1.4 点击应用右侧的“创建广告位”按钮或者进入“广告位管理页面”点击“添加广告位”按钮
![创建广告位](imgs/004.png)

#### 1.5填写相关信息，点击“添加”按钮，返回广告位管理列表页
![添加](imgs/005.png)

#### 1.6在广告位管理列表页，获取广告位的ID
![获取广告位](imgs/006.png)

## 2. 添加MoPub SDK和PlayableAds SDK，步骤如下：

了解如何使用[Cocoapods](https://guides.cocoapods.org/using/getting-started.html)

#### 2.1 在Podfile文件中添加依赖项
```
pod “mopub-ios-sdk”
pod “PlayableAds”
```
![依赖](imgs/007.png)

#### 2.2 在终端命令里面执行pod install
![依赖](imgs/008.png)

在安装完成后，关闭xcode，在工程根目录下打开.xcworkspace文件：

![依赖](imgs/009.png)

## 3. 将以下文件添加到工程里面

MPPlayableAdMobRewardedVideoCustomEvent.h

MPPlayableAdMobRewardedVideoCustomEvent.m

![依赖](imgs/010.png)

## 4. 在MoPub平台为可玩广告配置广告位
#### 4.1 为可玩广告新建广告位
- 进入应用，点击“new add unit”按钮

![new add unit](imgs/011.png)

- 创建广告位，请注意format应该为Rewarded video，点击“save”按钮

![Rewarded video](imgs/012.png) 

- 获取新创建广告位的ad unit ID

![创建广告位](imgs/013.png)

#### 4.2 获取已有广告位的ID
- 选择应用，进入广告位列表，选择要接入的广告位，点击进入。点击“edit ad unit”按钮，点击“view code integration”按钮

![view code integration](imgs/014.png)

- 获取广告位的ad unit ID

![获取广告位](imgs/015.png)

## 5. 在MoPub平台增加可玩广告为新的广告源
#### 5.1 进入“networks”页面，点击“add a network”按钮
![add a network](imgs/016.png)

#### 5.2 点击“custom native network“链接
![custom native network](imgs/017.png)

#### 5.3 添加可玩广告平台名称为ZPLAY Ads，并且在步骤3中申请的广告位中配置可玩广告（图示2和图示3）。

![配置](imgs/018.png)

- 请在图示2的位置添加如下信息：
```
MPPlayableAdMobRewardedVideoCustomEvent
```

- 请在图示3的位置添加在可玩广告平台申请的广告位信息，格式如下：
```
{
	"APPID": "iOSDemoApp",
	"AdUnitId": "iOSDemoAdUnit"
}
```
注意：将iOSDemoApp替换成您在可玩广告平台申请的APPID（步骤1.3），将iOSDemoAdUnit替换成您在可玩广告平台申请的AdUnitId（步骤1.6）。

## 6. 在MoPub平台打开可玩广告广告源
#### 6.1 进入“segments”页面，点击“Global Segment”链接
![Global Segment](imgs/019.png)

#### 6.2 找到接入可玩广告的应用（如示例中MediationMopub）及广告位（示例中的新可玩广告），打开可玩广告广告源（图中的turn on所示的按钮）

![turn on](imgs/020.png)

## 7. 确认可玩广告配置成功
进入6.2 中已经打开可玩广告源的广告位管理页面，如果成功配置，则会在ad sources列表中会显示如下信息。如果未显示，请参照以上步骤进行检查。

![确认可玩广告配置成功](imgs/021.png)

## 8. 在工程中使用MoPub请求可玩广告

配置信息如下：

![配置信息](imgs/022.png)

- 图示1：导入MoPub需要的文件
- 图示2：添加MoPub广告回调的声明
- 图示3：初始化MoPub SDK
- 图示4：请求广告，请正确填入在MoPub平台申请的广告位ID（详见第4步）
- 图示5：展示广告，请正确填入在MoPub平台申请的广告位ID（详见第4步）
- 图示6：添加MoPub广告回调接口

## 9. 调试
执行步骤8中图示4的方法，请求广告，查看log

![调试信息](imgs/023.png)

## 10. 示例
点击查看[Demo](https://github.com/zplayads/PlayableMopubAdDemo-iOS)

注意：执行demo前，请在终端命令行进入工程根目录下执行pod install。
