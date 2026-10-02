# 手写公式识别 (handwriting-math-recognizer)

Obsidian 插件：在笔记中手写公式，自动识别为 LaTeX，支持预览后一键插入。

## 功能特性

- **手写识别双通道**：本地 ONNX 模型（comer 公式识别模型）+ 云端大模型 API
- **接入国产模型**：内置 DeepSeek、智谱 GLM、通义千问、硅基流动、阶跃星辰等平台的预设配置（OpenAI 兼容接口）
- **预览后插入**：识别结果先实时渲染预览，确认后再插入；支持插入独立公式块 `$$...$$` 或行内公式 `$...$`
- **悬浮窗交互**：可拖动、可缩放（拖左下角手柄，矢量重绘），适配触屏/平板
- **移动端可用**（`isDesktopOnly: false`），针对平板触控输入做过优化

## 安装

1. 将本仓库的 `manifest.json`、`main.js`、`styles.css` 放入
   `.obsidian/plugins/handwriting-math-recognizer/` 目录
2. 在 Obsidian 设置 → 第三方插件中启用「手写公式识别」

> **注意**：本地识别依赖约 87MB 的模型文件（comer 的 `encoder_int8.onnx` / `decoder_int8.onnx` 与
> onnxruntime-web 的 `.wasm`）。为保持仓库轻量，这些二进制文件**未包含在本仓库**中，
> 仓库版本仅提供代码。未放置模型文件时，本地识别不可用，但**云端 API 识别模式完全可用**。

## 配置（云端 API）

在插件设置页：

1. 选择「服务提供商」（DeepSeek / 智谱 / 通义 / 硅基流动 / 阶跃星辰 等），自动填入接口地址与模型名
2. 填入你的 API Key
3. 识别方式选择「仅云端 API」或「自动（本地优先）」

## 使用

- 开启「手写模式」后，在笔记任意位置开始书写
- 点击「识别」，等待结果预览
- 点击「插入」把 LaTeX 写入光标位置（独立公式块或行内公式）

## 版权说明

- 代码与界面：见仓库 LICENSE
- 内置识别模型（comer 系列）与其运行时（onnxruntime-web）的许可信息见
  `vendor/LICENSE-ink-on.txt` 与 `vendor/NOTICES.md`（未随仓库分发，见上文说明）
