# <img src="app/appicon.svg" alt="PreySense logo" width="42" height="42" align="left"> PreySense

PreySense 是一款面向 Acer 掠夺者（Predator）笔记本的轻量级 Windows 工具，派生自 G-Helper。它可以快速、直接地控制性能模式、风扇、显卡超频、RGB 灯效、显示设置，并提供自定义的硬件悬浮窗，完全绕开臃肿的官方 Predator Sense 软件。

本项目属于实验性质，且与硬件强相关。它仅在有限的 Acer 掠夺者机型上进行过开发和测试，因此无法保证与其他 Acer 笔记本兼容。

> 本仓库为 **汉化版**：程序界面、提示对话框与本文档均已翻译为简体中文。

<p align="center">
  <img src="docs/pics/Prey Sense.png" alt="Prey Sense Interface" width="380"><br>
  <b>PreySense 主界面</b>
</p>

## 功能特性

- **性能模式**：在 **节能（Eco）**、**静音（Silent）**、**均衡（Balanced）**、**性能（Performance）** 和 **狂暴（Turbo）** 之间循环切换。
- **按模式独立配置**：每个性能模式可单独保存 CPU 功耗限制、显卡偏移量和自定义风扇曲线。在风扇曲线中按住 Ctrl 可让节点对齐吸附。
- **CPU 与显卡调校**：
  - 直接控制 CPU 功耗限制（PL1 / PL2）。
  - NVIDIA 显卡核心频率与显存频率超频偏移。
- **显卡模式切换**：在 **集显模式（Endurance，仅核显）**、**标准模式（Standard，核显 + 独显）** 和 **独显直连（Ultimate，独占独显）** 之间切换，并支持「电池供电时自动切换核显」开关。
- **掠夺者按键集成**：完整支持物理模式切换键与自定义快捷键。使用 掠夺者键 + 1~5 快速切换性能模式。
- **显示配置**：自动切换屏幕刷新率、LCD 过驱（Overdrive）控制，以及按刷新率保存的色彩配置。
- **电池管理**：充电上限控制，用于延长电池寿命。
- **键盘 RGB 控制**：支持键盘灯效调节。
- **紧凑硬件悬浮窗**：样式化的 HUD，实时显示 CPU/GPU 温度、风扇转速、功耗、内存/显存占用、FPS 计数器和功耗曲线。

<p align="center">
  <img src="docs/pics/Overlay.png" alt="Prey Sense Overlay" width="380"><br>
  <b>硬件性能悬浮窗</b>
</p>

## 运行要求

- **系统**：Windows 10 或 Windows 11 x64。
- **硬件**：具备兼容 Acer WMI 与 AcerService 接口的 Acer 掠夺者笔记本。
- **运行时**：Microsoft [.NET 10 Windows Desktop Runtime x64](https://dotnet.microsoft.com/download/dotnet/10.0)。
- **CPU 调校**：需安装 [PawnIO](https://pawnio.eu/) 驱动，用于底层 CPU MSR / 功耗限制访问。
- **RGB 调校**：需安装 Predator Sense 服务组件，键盘 RGB 控制才能生效。

## 下载与运行

1. 下载最新的 Release 版本。
2. 以**管理员身份**运行 `PreySense.exe`。

## 从源码构建

前置条件：安装 [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0)。

```powershell
dotnet build app\PreySense.csproj
```

## 技术文档

关于 WMI 调用、偏移量和灯光控制的详细文档位于 `docs` 目录：

- [Acer WMI 文档](docs/acer_wmi_documentation.md)
- [Acer Service RGB 协议](docs/acer_service_rgb.md)
- [已发现的 WMI 偏移量](docs/discovered_offsets.md)

### 注册表状态

用户配置文件、自定义风扇曲线和应用状态保存在：

```text
HKCU\SOFTWARE\PreySense
```

## 免责声明

PreySense 会控制笔记本硬件的底层行为（风扇、功耗限制、频率等）。请自行承担使用风险。不正确的设置可能导致系统不稳定或出现意外行为。
