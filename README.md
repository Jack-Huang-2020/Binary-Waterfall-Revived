# <img src="src/binary_waterfall/resources/icon.png" height="20px" alt="Binary Waterfall"/> Binary Waterfall Revived
### A Raw Data Media Player

<p align="center"><img src="docs/example.png" width="400px" alt="Running the program on mspaint.exe"/></p>

<p align="center"><a href="https://www.youtube.com/watch?v=NFe0aGO9-TE">Inspired by this video.</a></p>

## Attribution

If you use this program to make a video or other project, you must provide attribution. Attribution is required regardless of whether your project is for-profit or not. Please reproduce the following attribution statement in full in your video description or otherwise include it in the references for your project:

```Text
Made with the help of Binary Waterfall:
https://github.com/Jack-Huang-2020/Binary-Waterfall-Revived
```

## Keyboard Shortcuts

- **Open File**： Command / Ctrl + O
- **Close File**： Command / Ctrl + W
- **Play/Pause**: Spacebar
- **Frame Back / Left 15s**： ⬅️
- **Frame Forward / Right 15s**： ➡️
- **Restart**: R
- **Volume Up**： ⬆️
- **Volume Down**： ⬇️
- **Mute**: M
- **Scroll Up / Down （Fast）**： Mouse Wheel or . / ，
- **Scroll （Precise）**： Ctrl / Command + Wheel

## 项目架构 / Project Architecture

```
binary-waterfall/
├── binary-waterfall.py          # 入口文件
├── src/binary_waterfall/
│   ├── core.py                  # 应用初始化、暗色主题
│   ├── window.py                # 主窗口 UI、菜单、快捷键、设置
│   ├── generators.py            # 核心渲染引擎（CPU/GPU 像素转换）
│   ├── outputs.py               # 播放器控制和导出渲染
│   ├── dialogs.py               # 设置/导出/关于对话框
│   ├── widgets.py               # 自定义控件（ImageButton, SeekBar）
│   ├── constants/               # 常量配置
│   │   ├── colors.py            # 颜色主题
│   │   ├── defaults.py          # 默认参数
│   │   ├── enums.py             # 枚举定义
│   │   ├── links.py             # 链接配置
│   │   ├── paths.py             # 路径配置
│   │   ├── platform.py          # 平台检测
│   │   ├── resources.py         # 资源路径
│   │   ├── splash.py            # 启动画面配置
│   │   └── version.py           # 版本信息
│   ├── helpers/                 # 辅助函数
│   │   ├── colors.py            # 颜色处理
│   │   ├── general.py           # 通用工具
│   │   ├── images.py            # 图像处理
│   │   └── qt.py                # Qt 工具
│   └── resources/               # 资源文件
│       ├── *.svg                # SVG 图标
│       ├── icon.ico             # 程序图标
│       ├── splash.jpg           # 启动画面
│       └── watermark.png        # 水印
├── pyproject.toml               # 项目配置和依赖
├── build.bat / build_mac.sh     # 构建脚本
└── .github/workflows/build.yml  # CI 流水线
```