# 关于

游戏[火力全开](https://store.steampowered.com/app/4261400/_/)的MOD模板。

# 虚幻引擎版本

5.5

# 自定义地图

## 新建MOD文件夹

![新建MOD文件夹](https://github.com/user-attachments/assets/68f5ec33-5c85-4ea9-8f90-e28f7c182dd3)

在Mods目录下新建以“Mod_”开头的文件夹，该文件夹下的内容会被打包成一个Mod（一个pak文件）。为了避免与其他Mod冲突，该文件夹的名称应保持唯一，可以在末尾添加GUID，例如：Mod_Example_f829c3c7。

“Mod_*”文件夹内的资产不应该依赖文件夹外部的资产，因为外部的资产不会被打包进pak文件。

## 新建地图

新建Level资产，根据自己的需要创建地图内容。

## 放置 Actor

放置 NavMeshBoundsVolume Actor，用于生成AI导航网格。

放置 PlayerStart Actor，该Actor仅用于开始游戏前摄像机的位置。

在游玩区域下面放置 BP_KillZone Actor，可选，用于玩家角色不小心掉出地图时重生玩家。

![Actors](https://github.com/user-attachments/assets/af139adf-ef00-4996-b3c1-613a52a0dd67)

### 团队竞技模式

在队伍1出生区域放置多个 BP_SpawnPoint_Team1 Actor，用于队伍1的玩家出生点。

在队伍2出生区域放置多个 BP_SpawnPoint_Team2 Actor，用于队伍2的玩家出生点。

在地图多个位置放置 BP_PatrolPoint Actor，用于AI巡逻点。

![Actors](https://github.com/user-attachments/assets/6a2cc2b0-52dc-4dab-8208-196eb5feb095)

### 个人竞技模式

在地图多个位置放置 BP_PatrolPoint Actor，用于玩家出生点和AI巡逻点。

### 击杀确认模式

和团队竞技模式相同。

### 僵尸模式

和个人竞技模式相同。

## 创建地图的预览图

使用虚幻引擎自带的高清截图工具或其他方法创建地图的预览图纹理，用于在UI上显示。

![MapPreview](https://github.com/user-attachments/assets/3ccb3f44-23d4-45dc-86f7-9076e68ef718)

Texture Group 选择 UI。

![TextureGroup](https://github.com/user-attachments/assets/5580b564-93d0-4775-aef2-c5d2d5d8aca9)

## 新建自定义地图类

继承 BP_CustomMapBase 类创建子类，必须以“BP_CustomMap_”开头，例如：BP_CustomMap_Example。

类默认值中填写相关信息：

![CustomMap](https://github.com/user-attachments/assets/3eb7b46f-a5d0-44ec-a424-35d408446565)

MapID 地图的唯一标识，建议使用GUID。

MapName 用于在UI上显示的地图名称。

Map 引用新建的地图资产。

PreviewImage 引用地图的预览图纹理资产。

SupportedGameModes 指定该地图支持的游戏模式。

可用的游戏模式ID：

- GameMode.BuildIn.TeamDeathMatch
- GameMode.BuildIn.FreeForAll
- GameMode.BuildIn.Zombie
- GameMode.BuildIn.KillConfirmed

MapCapacity 仅用于僵尸模式，用于指定地图能同时容纳的最大僵尸个数。

IsMod 和 ModID 无需填写，主游戏负责填充。

## 创建 PrimaryAssetLabel 数据资产

该资产将导致所在文件内的所有内容被打包成单独的pak文件。

![AssetLabel](https://github.com/user-attachments/assets/bd80ac4e-6dc6-4444-927c-7465b65a4399)

![AssetLabel](https://github.com/user-attachments/assets/35cdc48a-84cc-4a7c-8c37-c4c13b7a00df)

## 打包

![Package](https://github.com/user-attachments/assets/560f066d-5afd-48e2-913d-8dd43deb9e71)

打包完成后生成pak文件。

![pak](https://github.com/user-attachments/assets/c44217d7-e9a7-43e7-b154-8fece0a12882)

## 本地测试

## 上传到创意工坊
