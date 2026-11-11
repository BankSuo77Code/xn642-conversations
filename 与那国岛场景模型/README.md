# 与那国岛场景模型

本包包含与那国岛三维场景的原始模型、纹理和配置，共 219 个文件。完整 ZIP 约 485 MiB。 [下载模型 ZIP](https://github.com/BankSuo77Code/xn642-conversations/releases/download/yonaguni-scene-model-v1/Yonaguni-Scene-Model.zip) · [查看 GitHub Release](https://github.com/BankSuo77Code/xn642-conversations/releases/tag/yonaguni-scene-model-v1)

解压后保留以下目录结构。

```text
yngd/
├── yonaguni_vis.osg
├── yonaguni_vis.flt
├── Config.ini
└── texture/
    ├── VIS_yonaguni/
    └── KRGB_yonaguni/
```

- `yonaguni_vis.osg` 可用支持 OpenSceneGraph 的查看器打开。模型本地坐标以米为单位，X 向东、Y 向北、Z 向上。
- `yonaguni_vis.flt` 可用支持 OpenFlight 的工具打开。两种格式均通过相对路径读取纹理，请保持 `texture` 与模型文件同级。
- `Config.ini` 保留模型中心位置和波段参数，可作为场景分析的参考。

下载后可用 SHA-256 核对压缩包。 [查看校验文件](./Yonaguni-Scene-Model-SHA256.txt)
