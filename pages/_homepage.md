# Live 2D Watcher

欢迎使用 Live 2D Watcher (L2DW) 。这是一款 [WebGAL](https://www.openwebgal.com/) 辅助工具。

由于目前（或者以前） WebGAL 的官方编辑器的「摆放立绘」和「切换 Live 2D 动作表情」不够便捷，故 L2DW 旨在提供一个「所见即所得」的操作体验，提高用户的编辑效率。

若您并非 WebGAL 用户，您也可以使用该软件「预览 Live2D 模型」与「自制动作表情」等。

## L2DW 能做什么

- 预览立绘 (Live2D 模型或纯图片)和背景。
- 预览 Live2D 模型的动作表情。
- 自制 Live2D 模型的动作表情。
- 自由摆放立绘和背景的位置，并一键生成代码。
- 支持堆叠子立绘（俗称「拼好模」）。
- 支持 WebGAL 同款滤镜效果。
- 快速重载 Live2D 贴图，方便改模时预览。
- 批量修改 Live2D 模型的动作表情路径。
- 支持修改 Live2D 模型部件的不透明度。
- 支持修改 Live2D 模型参数的初始值（如 `PARAM_IMPORT`）。
- 实时输出透明视频源(spout)，便于录制供后期使用。

## 准备工作

1. 下载并安装 [WebGAL Terre](https://www.openwebgal.com/zh-cn/download/) (WebGAL 官方编辑器) 。

  L2DW 虽然是 WebGAL 的辅助工具，但本身不提供编辑 WebGAL 游戏的功能，您仍然需要使用编辑器来创建和编辑游戏项目。

2. 学习一点点 WebGAL 脚本的编写方式。

  在 L2DW 里摆放好立绘，并设置好动作表情后，L2DW 会生成对应的 WebGAL 脚本代码，您需要将这些代码复制到 WebGAL 编辑器里，因此需要有一点点的编写 WebGAL 脚本的能力。您可以在 [WebGAL 官方文档](https://docs.openwebgal.com/webgal-script/base.html) 里学习相关内容。

## 兼容性

- 仅支持加载旧版 Live2D 模型 `*.json`，暂不支持新版 Live2D 模型 `*.model3.json` 。
