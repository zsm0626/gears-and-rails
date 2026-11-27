# 齿轮与钢轨（Gears & Rails）

一个以 **Create 机械动力** 为核心的铁路/列车整合包，从蒸汽时代一路开到中国高铁。

---

## 版本信息

| 项目 | 值 |
|---|---|
| Minecraft | 1.21.1 |
| NeoForge | 21.1.267 |
| 模组数量 | 83 个 |
| 任务书 | 19 章 / 285 任务 |
| 整合包版本 | v1.0.0 |

---

## 核心特色

### 铁路主线

- **蒸汽 → 内燃 → 电气 → 高铁** 完整科技树
- **CRH 中国高铁**（CRH1A / CRH2A / CR200J），最高 200 km/h
- **RailX 柔性轨道**（任意角度 + 外轨超高倾斜）
- **汽鸣铁道 / TSU**（37 个车站设备）
- **Create Railways Navigator**（线路导航）

### 任务书

- **19 章 / 285 个任务**
- 从「铁与火」到「高铁时代」完整引导
- 详细步骤 + 颜色标注 + 奖励系统

### 工业体系

- Create 6.0.10 本体
- TFMG（石油化工）
- Create Addition（电气化）
- Create Diesel Generators（柴油）
- Create Big Cannons（火炮）

### 建筑与装饰

- Design n' Decor / Interiors（内饰）
- Create Deco / Copycats（装饰）
- Escalated（扶梯、电梯）
- WorldEdit / Effortless Building（建筑）

### 性能优化

- Sodium + Iris（渲染 + 光影）
- Voxy + Roxy（远景渲染）
- ModernFix / FerriteCore / EntityCulling

### 汉化

- I18nUpdateMod（自动汉化）
- 语言包补充

---

## 安装方法

### PCL 启动器

1. 打开 PCL
2. 版本管理 → 导入整合包
3. 选择 `.mrpack` 文件
4. 等待自动下载 NeoForge 和模组

### 手动安装

1. 安装 Minecraft 1.21.1 + NeoForge 21.1.267
2. 解压 `.mrpack` 里的 `overrides/` 到游戏目录
3. 启动

---

## 模组列表（83 个）

### Create 核心（12）
- Create 6.0.10
- Create Addition
- Create Big Cannons
- Create Deco
- Create Diesel Generators
- Create Ore Excavation
- Create BB（转向架）
- Create Connected
- Create Jetpack Curios
- Create Mechanical Extruder
- Create Train Physics
- TFMG

### 铁路（7）
- RailX
- Railways（汽鸣铁道）
- CRH（Hexie）
- TSU（Trains System Utilities）
- Create Railways Navigator
- Useful Railroads
- Create Train Physics

### FTB（5）
- FTB Library
- FTB Quests
- FTB Teams
- FTB XMod Compat
- FTB Chunks

### 优化（8）
- Sodium
- Iris
- Voxy
- Roxy
- EntityCulling
- FerriteCore
- ModernFix
- ImmediatelyFast

### 饰品背包（7）
- Curios
- Artifacts
- Cosmetic Armor Reworked
- Sophisticated Backpacks
- Sophisticated Core
- Traveler's Backpack
- Create Jetpack Curios

### 建筑装饰（7）
- Design n' Decor
- Interiors
- Copycats
- Escalated
- Builders Wands
- WorldEdit
- Effortless Building

### 其他（37）
- 详见 `.mrpack` 内的 `overrides/mods/` 目录

---

## 光影推荐

| 光影 | 用途 |
|---|---|
| Complementary Reimagined | 日常（推荐） |
| Rethinking Voxels | 体素光追（高级） |
| BSL | 经典 |
| Photon | 截图 |

---

## 材质包

- Create Ultra（Create 机器高清）
- JICKLUS（基础方块）
- Fast Better Grass（草）
- Borderless Glass（玻璃）

---

## 已知问题

### ⚠️ TSU 视频功能导致崩溃（重要）

**症状**：

- 进入主菜单后 **10~20 秒游戏闪退**
- **没有 crash-report**（`crash-reports` 文件夹是空的）
- PCL 显示返回值 `-2147483645`（`0x80000003`）
- Windows 事件查看器里 `Faulting module name: libcef.dll`

**原因**：

TSU（trainsystemutilities）内置了 **Manta 视频功能**（内嵌 Chromium/CEF）。
游戏启动时它会自动预热视频运行时，如果你的显卡/驱动环境下 **GPU 子进程起不来**，
Chromium 判定「GPU 不可用」后直接 FATAL，触发断点异常，**把整个游戏进程杀掉**。

**注意**：这不是 Java 模组报错，所以启动器的日志分析会显示「未找到原因」。

**解决方案**：

```
1. 打开整合包目录：
   .minecraft\versions\齿轮与钢轨\

2. 找到文件夹：
   mcss-chrome-native

3. 把里面的所有内容删掉
   （或者把整个文件夹改名为 mcss-chrome-native.disabled）

4. 重启游戏
```

**影响**：

- ✅ 视频播放功能关闭（不会再崩）
- ✅ 车站大屏、动态、调度、供电等 **TSU 其他功能全部保留**

**如果重启后文件夹又被重新生成**：

说明 TSU 每次启动都会解包 CEF。此时需要：

- 换 **Java 21**（NeoForge 21.1 官方目标版本，Java 25 可能有问题）
- 或者等 TSU 作者修复（报给作者：CEF 应支持 `--disable-gpu` 降级，不该 FATAL 宿主进程）

---

### 其他小问题

- **RailX 的 cant（倾斜）**：需要**扳手**交互，且数值框只在柔性轨道端点出现（中间是普通曲线）
- **Voxy 和部分光影**：可能有兼容性问题（建议用 Complementary）
- **JICKLUS 材质包**：`tall_grass.json` 有 JSON 格式错误（可能导致部分草方块显示异常），可移出资源包
- **TSU 自有资源**：缺 `font/gui.ttf`，部分贴图 1254×1254 超过图集上限（模型缺图，不影响玩法）

---

## 许可证

整合包本身：MIT
各模组：遵循各自原作者许可证

**禁止商用，仅供个人游玩。**

---

## 致谢

感谢所有模组的原作者：
- Create 团队
- RailX（lhwdev）
- CRH（WillowKoishi）
- 汽鸣铁道团队
- FTB 团队
- 以及所有贡献者
