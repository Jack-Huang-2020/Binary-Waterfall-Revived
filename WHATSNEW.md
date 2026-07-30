# 更新日志 / Changelog

## 最新版本 - 5.1.3 (2026-07)

### 新增功能 / New Features
- **多核并行 CPU 像素渲染**：使用 `ThreadPoolExecutor` 将帧渲染任务拆分到多行并行处理，大幅加快大尺寸画面的生成速度 — `generators.py`
- **GPU 加速像素转换**：集成 PyTorch，支持 CUDA (NVIDIA) 和 MPS (Apple Silicon) 硬件加速 — `generators.py`
- **播放头 (Playhead) 叠加层**：在瀑布显示画面上标记当前播放行，支持反色 + 降低饱和度 + 亮度对比增强 — `generators.py`
- **拖拽打开文件**：支持从文件管理器拖放文件到主窗口或播放器标签上打开 — `window.py`
- **最近文件菜单**：保存最近打开的 10 个文件，支持持久化存储和清空历史 — `window.py`
- **自定义颜色格式**：支持 RGB/灰度通道映射，包括 `{r}{g}{b}{w}{u}` 及大小写反转 — `generators.py`
- **视频编码器设置对话框**：导出视频时可选择编码器、音频编码器、编码预设 — `dialogs.py`
- **关于对话框**：显示程序名称、版本、版权等信息 — `dialogs.py`
- **设置重置为默认值**：在音频/视频/播放器设置对话框中提供重置按钮 — `dialogs.py`
- **SVG 图标**：播放、暂停、前进、后退、重启、音量等全部使用 SVG 矢量图标 — `resources/`

### 功能改进 / Enhancements
- **平滑滚动**：鼠标滚轮支持加速滚动（滚动速度越快，行数越多），Ctrl+滚轮精确滚动 1 行 — `window.py`
- **键盘快捷键**：Space=播放/暂停，←→=快退/快进15秒，↑↓=音量±5%，M=静音切换，R=重启，逗号/句点=逐帧 — `window.py`
- **拖放文件打开**：支持 macOS 触控板像素级滚动检测 — `window.py`
- **线程安全的文件访问**：使用 `threading.Lock` 确保多线程渲染时文件指针安全 — `generators.py`
- **图像/视频翻转**：支持垂直和水平翻转 — `generators.py`, `window.py`
- **视频/音频对齐模式**：支持 End/Middle/Start 三种对齐方式 — `generators.py`
- **流式文件读取**：不再将整个文件加载到内存，改为按需读取 — `generators.py`
- **进度条优化**：导出时显示更细粒度的进度信息 — `helpers/qt.py`
- **音量图标点击切换静音** — `window.py`
- **窗口大小自适应**：根据控件内容自动调整窗口尺寸 — `window.py`
- **记住上次保存/打开位置** — `window.py`
- **导出完成对话框**：导出成功/失败/取消均有提示 — `window.py`
- **热键信息对话框**：显示所有键盘快捷键说明 — `dialogs.py`

### Bug 修复 / Bug Fixes
- **修复快速滚动热键标签错误** — `dialogs.py`
- **修复 PROJECT_URL 指向错误的 GitHub 仓库** — `constants/links.py`
- **修复版本字符串格式**：标准化为 semver 格式 — `version.yml`
- **修复版权字符串中包含非法字符** — `version.yml`
- **修复同步中帧末尾实际是中间的重大错误** — `generators.py`
- **修复更改音频设置时的 bug** — `window.py`
- **修复颜色反转错误** — `generators.py`
- **修复"强制宽高比"失效的问题** — `outputs.py`
- **修复红蓝通道默认交换的问题** — `generators.py`
- **修复音量控制 bug** — `generators.py`
- **修复窗口更新时的模态问题** — `window.py`
- **修复图标更新问题** — `window.py`
- **修复图片加载兼容性**：更新 moviepy v2.x 导入路径，为 Python 3.14 添加 audioop-lts — `outputs.py`

### 构建与 CI / Build & CI
- **GitHub Actions 构建流水线**：自动化测试、构建和发布 — `.github/workflows/build.yml`
- **macOS .app 打包为 .tar.gz** 上传构建产物 — `build_mac.sh`
- **PyPI 发布脚本**：支持上传到 PyPI — `build_pypi.bat`
- **PyInstaller 打包**：支持 Windows .exe 和 macOS .app — `build.bat`, `build_mac.sh`
- **启动画面 (Splash Screen)**：PyInstaller 打包版本显示启动画面 — `resources/splash.jpg`
- **选择性平台构建**：仅在有版本标签时创建 GitHub Release，标记为预发布 — CI 配置
- **添加 PyTorch 依赖**：在构建流程中集成 CUDA/MPS 支持 — CI 配置

### 中文化 / Chinese Support
- 首次在 `README.md` 中添加中文说明
- 修改 README 中的项目名称和版权归属（Binary Waterfall Revived）
- 界面菜单、对话框、错误提示全部使用英文（国际化尚未完全支持中文）

---

## 历史版本 / Previous Versions

### v4.0 - Binary Waterfall Revived 品牌重塑
- 项目更名为 **Binary Waterfall Revived**
- 版本号提升至 4.0.0
- 添加键盘快捷键和鼠标滚轮导航
- 实现平滑滚动和精确滚动
- 添加最近文件菜单
- 热键信息对话框更新

### v3.x - 功能完善期
- 添加视频导出功能（MP4/AVI）
- 添加音频导出功能（MP3/WAV/FLAC）
- 添加图片序列导出功能
- 添加编码器设置对话框
- 添加翻转设置（水平和垂直）
- 添加视频/音频对齐选项
- 添加水印功能
- 添加关于对话框
- 改进进度条和导出对话框

### v2.x - PyQt5 重构
- 从 TKinter 迁移到 PyQt5 框架
- 替换 Pygame 为 mutagen + PyQt5
- 添加音频播放和音量控制
- 添加文件打开/关闭对话框
- 添加音视频设置面板
- 添加播放器设置面板
- 支持 SVG 图标按钮

### v1.x - 初始版本 (Pygame)
- 使用 Pygame 实现基础二进制瀑布可视化
- 读取二进制文件并生成 WAV 音频
- 将文件数据渲染为彩色图像
- 支持音视频同步播放
- 基本的窗口大小控制
- 暂停播放功能
- 音量控制
- 自定义颜色格式

---

*Note: This changelog is generated from source code analysis, grouped by actual functionality implemented.*