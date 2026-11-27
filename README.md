# FaceSwapLocal (本地换脸)

本地运行的 Android 换脸应用，使用 ONNX Runtime + InsightFace 模型。

## 构建

使用 GitHub Actions 自动构建 Debug APK：

1. 将本项目推送到 GitHub 仓库（main 或 master 分支）
2. 在 Actions 标签页手动触发或 push 后自动运行
3. 完成后在 Artifacts 中下载 `FaceSwapLocal-APK`

本地构建需要 Android SDK (API 34) + JDK 17：

```bash
./gradlew assembleDebug
```

APK 输出位置：`app/build/outputs/apk/debug/app-debug.apk`

## 使用说明

首次使用点「下载模型」按钮（约 400 MB：检测 det_500m、识别 w600k_r50、换脸 inswapper_128_fp16），
需要保持网络连接，断了再点一次会续传。也可以用「从手机文件导入模型」手动导入。支持图片与视频换脸。

注意：识别模型必须是 **w600k_r50**（buffalo_l 里的），不能用 buffalo_s 的 w600k_mbf——
两者的特征空间不通用，混用会导致换出来的脸不像来源照片里的人。
