# 海岛数境 · 仿真数据集一键生成软件 v1.0.1

一键生成视点轨迹，驱动 COSSIM 批量采集图像。

- 参数记忆覆盖海岛地物俯视、靠岸舰船观测、采样间隔和每视点停留时间。软件重启后恢复当前 Windows 用户上次保存的参数。
- 与那国岛底图支持滚轮缩放、拖动平移、“全岛”和“定位视点”。底图由项目三维场景的纹理生成。
- 导出采用 14 列、GBK 编码的 CSV。在 COSSIM 的传感器自定义轨迹中加载后，即可按轨迹采集图像。

下载 Windows x64 含底图版并完整解压。[下载 ZIP](./HaidaoViewpointTrajectory-v1.0.1-win-x64-with-map.zip?raw=true)

双击 `HaidaoViewpointTrajectory.exe`，保留同目录的 `_internal` 和 `maps`。Python 与图形组件已随包提供。

可核对下载文件的 SHA-256。[校验文件](./SHA256SUMS-v1.0.1.txt) 解压目录内附有使用说明和第三方许可。
