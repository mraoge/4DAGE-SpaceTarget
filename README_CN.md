# Space Targets in Unity
SpaceTarget是一个支持空间识别定位的插件。通过使用4DKK-Pro三维相机作为空间建模的采集工具，将生成的模型数据作为空间识别的识别数据，你可以轻松地将AR增强现实内容无缝叠加到现实环境中。通过此插件可以创建游戏、导航应用、空间标示，并应用在办公室、工厂车间、公寓、公共场所、博物馆等不同空间场所。

![space target](https://github.com/Zwt-hello/4DAGE-SpaceTarget/blob/master/Document/image/view.gif)


此SDK中不包含空间目标数据，你需要使用支持的设备采集创建您自己的空间数据。请参阅[数据采集](http://... "数据采集")文档，以了解更多信息。

# 要求
> - 支持的Unity Editor
`Unity2019.4 +`

------------
> - Api Compatibility Level 请选择 
`.NET4.X`

------------

> - 安卓系统
`Android 7.0 +`

------------

> - iOS系统
 `iOS 12 +`

# 安装
你可以选择使用 **unitypackage** 包安装或者 **UPM** 的方式。
### UnityPackage
[Download Package](http://... "从官网下载package")

### Unity Package Manager
在 **Packages/manifest.json** 添加
```
{
   " dependencies " : {
     "com.4dage.spacetarget": "https://github.com/Zwt-hello/4DAGE-SpaceTarget.git#upm"
  }
}
```
或者在编辑器中打开 **Package Manager** ，点击 **+** ， 选择 **Add package from git URL** , 输入  `https://github.com/Zwt-hello/4DAGE-SpaceTarget.git#upm`

# 功能
- 支持空间识别和环境跟踪功能
- 支持ARKit、ARCore
- 支持第三方AR拓展接入

# 快速开始
使用ARKit/ARCore
> SDK已集成对ARKit、ARCore的支持，若您已有支持的设备，可直接使用SDK构建Android/iOS应用。
- [查看安卓支持的设备](https://developers.google.com/ar/devices "查看安卓支持的设备")
- [查看苹果支持的设备](https://www.apple.com.cn/augmented-reality/ "查看苹果支持的设备")

## 创建Target
1. 首先在 Unity 中创建并打开一个新项目。有关支持的 Unity Editor 版本，请参阅支持的版本。

1. 向场景中添加**ARFoundation**(ARKit、ARCore)组件
	> GameObject -> XR -> AR Session
	
	> GameObject -> XR -> AR Session Origin

1. 创建一个Space Target对象，并添加`ARFoundationManager.cs`脚本，并指定相关的参数
	>  GameObject -> 4DAGE-SpaceTarget -> Space Target

	> ![](https://github.com/Zwt-hello/4DAGE-SpaceTarget/blob/master/Document/image/t1.jpg)

	**查看案例场景**
	```
	Assets/4DAGE-SpaceTarget/Samples/Base on ARFoundation Example/Scene/SpaceTarget-base on ARFoundation Example
	```

## 配置Target
1. 点击**Add Database** 按钮，打开database下载UI面板

	*如何获取数据？请参阅[数据采集](http://... "数据采集")
	请查看具体的采集教程，请根据教程采集空间数据。
	若一切顺利，完成采集待数据云端计算完成后，你将会得到一个采集完成的结果*

	例如：https://www.4dkankan.com/spc.html?m=Html34yLt
	
	那么Target data ID 则为 `Html34yLt` , 请输入该ID以下载数据。

	![](https://github.com/Zwt-hello/4DAGE-SpaceTarget/blob/master/Document/image/t3.jpg)

1. 在SpaceTarget对象上选择您已下载的空间数据

	![](https://github.com/Zwt-hello/4DAGE-SpaceTarget/blob/master/Document/image/t2.jpg)

	参数说明：

	>`World Center Mode` ：
	>
	>**DEVICE** *模式下，为了匹配真实世界，Target会随时改变位置*
	>
	>**TARGET** *模式下，Target位置不会发生改变，需要指定ARCamera的根节点*

	>`Visible Database` : *在真实世界中显示/隐藏识别数据*
	
	>`Add Occlusion` ：*添加深度遮挡，勾选后在真实世界中可以对3D内容实现遮挡*
	
	>`Transparent Database` ：*模型透明*
	
	>`Show Outline` ： *显示模型描边*

1. 添加您的3D内容到场景中，并将内容作为SpaceTarget的**子物体**
![](https://github.com/Zwt-hello/4DAGE-SpaceTarget/blob/master/Document/image/t4.jpg)

## 构建项目
### 基本设置
1. 选择您需要构建的平台（Android/iOS）

1. 请将Player Settings -> Api Compatibility Level 设置为 .NET 4.x , 如果构建Android，请将Android Minimum API Level 设置为 Android 7.0 以上。

	![](https://github.com/Zwt-hello/4DAGE-SpaceTarget/blob/master/Document/image/t5.jpg)

1. Enjoy yourself!

### 注意事项

**如果构建平台为Android,请阅读以下内容**

Google ARCore 为了支持 Android 11（API 级别 30），在 Unity 2018.4 或更高版本中使用这些版本的ARCore 时，需要 Gradle 5.6.4 或更高版本。具体参阅[ARCore主页](https://developers.google.com/ar/develop/unity/android-11-build "ARCore主页")，请参照以下文档设置您的项目，以保证安卓编译成功。

#### Unity 2020.1 或更高版本

这些版本是使用 Gradle 5.6.4 或更高版本以及 Gradle 插件 3.6.0 或更高版本构建的。无需任何操作。

#### Unity 2019.4 系列版本

1. 转到Preferences > External Tools > Android > Gradle ，并将自定义Gradle设置为 Gradle 5.6.4或更高版本。有关下载，请参阅[Gradle构建工具](https://gradle.org/releases/ "Gradle构建工具")。

	![](https://github.com/Zwt-hello/4DAGE-SpaceTarget/blob/master/Document/image/a1.png)

1. 转到Project Settings > Player > Android tab > Publishing Settings > Build ，然后选择两者：

	`Custom Main Gradle Template`
	
	`Custom Launcher Gradle Template`

	![](https://github.com/Zwt-hello/4DAGE-SpaceTarget/blob/master/Document/image/a2.png)

1. 对两个生成的文件应用以下更改：

	`Assets/Plugins/Android/mainTemplate.gradle`

	`Assets/Plugins/Android/launcherTemplate.gradle`

	分别打开这两个文件，如果顶部存在以下注释，请删除该注释：
	```
	// GENERATED BY UNITY. REMOVE THIS COMMENT TO PREVENT OVERWRITING WHEN EXPORTING AGAIN
	```
	在文件顶部插入以下几行：
	```
	buildscript {
		repositories {
			google()
			jcenter()
		}
		dependencies {
			// Must be Android Gradle Plugin 3.6.0 or later. For a list of
			// compatible Gradle versions refer to:
			// https://developer.android.com/studio/releases/gradle-plugin
			classpath 'com.android.tools.build:gradle:3.6.0'
		}
	}

	allprojects {
	   repositories {
		  google()
		  jcenter()
		  flatDir {
			dirs 'libs'
		  }
	   }
	}
	```

# 使用自定义AR SDK

SpaceTarget 提供了接入第三方AR SDK 功能，可以根据开发者的需求，接入第三方ARSDK比如[EasyAR](https://www.easyar.cn/ "EasyAR") , [Vuforia](https://developer.vuforia.com/ "Vuforia")等。同时也可以接入第三方MR眼镜，比如[NReal](https://developer.nreal.ai/ "NReal ")。

## 接入说明

接入前您需要了解以下内容，确保所接入SDK能够提供以下内容

- **Intrinsics**

```
	相机内参：
	-  Resolution: RGB(AR)相机输出的RawTexture的图像分辨率，类型：Vector2
	-  FocalLength: RGB(AR)相机输出的RawTexture的图像焦距，类型：Vector2
	-  PrincipalPoint: RGB(AR)相机输出的RawTexture的图像焦点位置，类型：Vector2
```

- **Pose**

```
	相机实时位姿：
	- Position: RGB(AR)相机的实时位移值，类型：Vector3
	- Rotation: RGB(AR)相机的实时旋转值，类型：Quaternion
```

- **RawTexture**

```
	原始图像:
	- RawImage：RGB(AR)相机的原始图像数据，类型：Byte[]
```

## 快速接入

若能满足接入说明的要求，即可以按照以下步骤在您新的工程中接入第三方SDK。

### Interface

接口脚本：`IARBase.cs`

```csharp
namespace SpaceTarget.Runtime
{
	public interface IARBase
	{
		Pose ARCameraTrackingPose();
		ARBaseCameraIntrinsics ARCameraIntrinsics();
		ARBaseCameraImageData ARCameraRawImageData();
		ARBaseSessionTrackingState ARSessionTrackingState();
	}
}
```

接口说明：

1.  **Pose ARCameraTrackingPose()**

	相机位姿，返回值为`UnityEngine.Pose`

1.  **ARBaseCameraIntrinsics ARCameraIntrinsics()**

	相机内参，返回值为`SpaceTaget.Runtime.ARBaseCameraIntrinsics`

	```csharp
	public struct Intrinsics
	{
		public Vector2Int resolution;
		public Vector2 focalLength;
		public Vector2 principalPoint;
	}
	```

1.  **ARBaseCameraImageData ARCameraRawImageData()**

	图像数据，返回值为`SpaceTarget.Runtime.ARBaseCameraImageData`

	```csharp
	public struct CameraImageData
	{
		public byte[] rawImageData;
		public SupportedTextureFormat supportedTextureFormat;
		public CameraImageOrientation rawImageOrientation;
	}
	public enum SupportedTextureFormat
	{
		RGBA32 = 0,
		RGB24 = 1
	}
	public enum CameraImageOrientation 
	{
		NONE = 0,
		UPSIDE_DOWN = 1,
		LEFT = 2,
		RIGHT = 3
	}
	```

	***枚举参数选择说明***

	`SupportedTextureFormat`：支持的图像格式。请根据获取的图像`rawImageData`选择相应的格式，目前支持`RGBA32`和`RGB24`两种格式的图像数据。

	`CameraImageOrientation`：相机原始图像的旋转方向。请根据获取的图像`rawImageData`选择正确的朝向。

	***如何确认图像朝向？***

	通常从CPU获取的原始图像并不是我们肉眼看到的“正常”朝向。每个ARSDK由于算法的不一样，朝向都可能是不一致的，因此最快确认朝向的方法是将获取到的`rawImageData`Encoding保存为图片到本地查看其朝向。

	- 假设图像如下图是正常朝向，则选择 `CameraImageOrientation = NONE`

		![](https://github.com/Zwt-hello/4DAGE-SpaceTarget/blob/master/Document/image/t61.jpg)

	- 假设图像如下图是向左朝向，则选择 `CameraImageOrientation = LEFT`

		![](https://github.com/Zwt-hello/4DAGE-SpaceTarget/blob/master/Document/image/t62.jpg)

	- 假设图像如下图是向右朝向，则选择 `CameraImageOrientation = RIGHT`

		![](https://github.com/Zwt-hello/4DAGE-SpaceTarget/blob/master/Document/image/t63.jpg)

	- 假设图像如下图是上下反转，则选择 `CameraImageOrientation = UPSIDE_DOWN`

		![](https://github.com/Zwt-hello/4DAGE-SpaceTarget/blob/master/Document/image/t64.jpg)

1.  **ARBaseSessionTrackingState ARSessionTrackingState()**

	ARSession的跟踪状态，返回值为`SpaceTarget.Runtime.ARBaseSessionTrackingState`

	```csharp
	public enum ARBaseSessionTrackingState 
	{
		NONE = 0,
		LIMITED = 1,
		TRACKING = 2
	}
	```


### Interface Implemention

1. 实现接口

	> 根据以上的接口说明，请根据第三方SDK各自的特性具体实现接口`IARBase.cs`

	模板：

	> SpaceTarget也提供了接口实现模板 [ThirdPartyARInterfaceTemplate.cs](http://... "ThirdPartyARInterfaceTemplate.cs")

	需要具体的实现案例参考？

	> 具体实现案例可参考SpaceTarget中ARKit、ARCore的接口实现 [ARFoundationImplemention.cs](http://... "ARFoundationImplemention.cs")

1. 为实现的接口创建接口实体

	接口实体的继承基类 `IARBaseProvider.cs`：

	```csharp
	namespace SpaceTarget.Runtime
	{
		public interface IARBaseProvider
		{
			IARBase Create();
		}
	}
	```

	例如你已实现了接口 `ThirdPartyARInterfaceTemplate.cs` ，则此接口实体为:

	```csharp
	public class ThirdPartyARProviderTemplate : IARBaseProvider
	{
		public IARBase Create()
		{
			return new ThirdPartyARInterfaceTemplate();
		}
	}
	```

### Interface Instance

接口实现后，恭喜你，你只需几行代码即可实现调用。

```csharp
[SerializeField] SpaceTargetBehaviour spaceTargetBehaviour;
// Start is called before the first frame update
public virtual void Start()
{
	if (spaceTargetBehaviour != null)
	{
		IARBaseProvider mARProvider = new ThirdPartyARProviderTemplate();
		spaceTargetBehaviour.StartTracking(mARProvider);
	}
}
```

## 案例参考
//to do

