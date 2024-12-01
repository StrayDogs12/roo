# Roop

> 通过这个软件，你可以将视频中的面部替换为你选择的任何面部。只需要提供一张目标面部的图片，无需数据集或训练。

[![构建状态](https://img.shields.io/github/actions/workflow/status/s0md3v/roop/ci.yml.svg?branch=main)](https://github.com/s0md3v/roop/actions?query=workflow:ci)

<img src="https://i.ibb.co/4RdPYwQ/Untitled.jpg"/>

## 安装

请注意，安装过程需要一定的技术能力，适合有一定经验的用户，不适合初学者。请勿在GitHub上提交与平台或安装相关的问题。

[基础版安装](https://github.com/s0md3v/roop/wiki/1.-Installation) - 安装后可能会运行较慢，但能在大多数计算机上运行。

[加速版安装](https://github.com/s0md3v/roop/wiki/2.-Acceleration) - 发挥CPU和GPU的最大性能，提升运行速度。

## MACOS下使用方法
```
Python
brew install python@3.10

PIP
python -m ensurepip

GIT
brew install git

FFmpeg
brew install ffmpeg
```

## 加速

### 加速配置指南

#### 1. **CUDA（Nvidia）**
要在Nvidia GPU上使用加速，需安装CUDA Toolkit 11.8和cuDNN（适用于CUDA 11.x版本）。

**安装依赖项：**

```bash
pip uninstall onnxruntime onnxruntime-gpu
pip install onnxruntime-gpu==1.15.1
```

如果CUDA提供者可用，使用以下命令：

```bash
python run.py --execution-provider cuda
```

---

##### Apple Silicon（苹果芯片）
如果你使用的是苹果自家的M1或M2芯片，需安装以下依赖：

**安装依赖项：**

```bash
pip uninstall onnxruntime onnxruntime-silicon
pip install onnxruntime-silicon==1.13.1
```

如果CoreML提供者可用，使用以下命令：

```bash
python run.py --execution-provider coreml
```

##### Apple 传统硬件（Intel芯片）
对于使用Intel芯片的苹果设备，安装以下依赖：

**安装依赖项：**

```bash
pip uninstall onnxruntime onnxruntime-coreml
pip install onnxruntime-coreml==1.13.1
```

如果CoreML提供者可用，使用以下命令：

```bash
python run.py --execution-provider coreml
```

#### 3. **DirectML（Windows）**
Windows用户可以使用DirectML进行加速。

**安装依赖项：**

```bash
pip uninstall onnxruntime onnxruntime-directml
pip install onnxruntime-directml==1.15.1
```

如果DirectML提供者可用，使用以下命令：

```bash
python run.py --execution-provider dml
```

---

#### 4. **OpenVINO（Intel）**
Intel的OpenVINO框架也可用于加速。

**安装依赖项：**

```bash
pip uninstall onnxruntime onnxruntime-openvino
pip install onnxruntime-openvino==1.15.0
```

如果OpenVINO提供者可用，使用以下命令：

```bash
python run.py --execution-provider openvino
```


## 启动
启动程序时，可使用以下命令和参数：

```
python run.py [选项]

-h, --help                                                                 显示帮助信息并退出
-s SOURCE_PATH, --source SOURCE_PATH                                       选择源图片
-t TARGET_PATH, --target TARGET_PATH                                       选择目标图片或视频
-o OUTPUT_PATH, --output OUTPUT_PATH                                       选择输出文件或目录
--frame-processor FRAME_PROCESSOR [FRAME_PROCESSOR ...]                    选择帧处理器（可选：face_swapper, face_enhancer 等）
--keep-fps                                                                 保持目标帧率
--keep-frames                                                              保留临时帧文件
--skip-audio                                                               跳过目标视频的音频
--many-faces                                                               处理视频中的所有面部
--reference-face-position REFERENCE_FACE_POSITION                          参考面部的位置
--reference-frame-number REFERENCE_FRAME_NUMBER                            参考帧的帧编号
--similar-face-distance SIMILAR_FACE_DISTANCE                              面部识别时使用的距离阈值
--temp-frame-format {jpg,png}                                              提取帧时的图像格式
--temp-frame-quality [0-100]                                               提取帧时的图像质量
--output-video-encoder {libx264,libx265,libvpx-vp9,h264_nvenc,hevc_nvenc}  输出视频的编码器
--output-video-quality [0-100]                                             输出视频的质量
--max-memory MAX_MEMORY                                                    最大内存使用量（以GB为单位）
--execution-provider {cpu} [{cpu} ...]                                     可用的执行提供者（选择：cpu 等）
--execution-threads EXECUTION_THREADS                                      执行线程数量
-v, --version                                                              显示程序版本并退出
```

### 无头模式

通过使用 `-s/--source`、`-t/--target` 和 `-o/--output` 参数，可以在无头模式下运行程序。

## 免责声明

本软件旨在积极推动AI生成媒体行业的发展，帮助艺术家完成角色动画、服装模型等工作。

我们认识到潜在的伦理问题，并已采取措施防止软件被用于不当内容（如裸露等）。用户应遵守当地法律并负责任地使用软件。如果使用真实面部图像，请事先获得许可，并在分享深度伪造内容时明确标注。开发者不对用户的行为负责。


## 致谢

- [deepinsight](https://github.com/deepinsight) 提供了 [insightface](https://github.com/deepinsight/insightface) 项目，这为我们提供了高质量的库和模型。

## 文档

详细文档请参阅 [文档](https://github.com/s0md3v/roop/wiki)。