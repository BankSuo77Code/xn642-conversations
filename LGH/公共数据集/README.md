# 已下载公共数据集参数与使用安排

更新日期：2026-11-12。依据本地下载校验记录和实际图像文件头整理，统计范围为本次选取的子集。

**主要使用前四个数据集：NWPU-RESISC45、OpenEarthMap、xBD、Coast Train，合计 1,663 张 RGB 图块。USGS Oregon 和 Galápagos 作为补充数据，合计 10 幅大幅正射影像。**

**本目录仅保存参数、来源链接和使用说明，不上传数据集图片、标签、压缩包、NPZ、Parquet 或其他数据文件。数据集本身保留在本地。**

## 1. 参数总览

像素尺寸均为“宽 × 高”，没有将后续裁片或模型生成图像计入原始数量。

| 顺序 | 使用安排 | 数据集（原下载编号） | 本次选取范围 | 实际数量 | 像素尺寸 | 通道与文件格式 |
|---|---|---|---|---:|---|---|
| 1 | **主要使用** | NWPU-RESISC45（D01） | island 海岛场景类 | 700 张 | 256 × 256 | RGB，JPEG |
| 2 | **主要使用** | OpenEarthMap（D06） | Mahe、Tonga、Zanzibar，来自 OpenEarthMap_wo_xBD | 286 张 | 1024 × 1024 | RGB，TIFF |
| 3 | **主要使用** | xBD / xView2（D16） | Lower Puna、Palu、Sunda 三个事件的灾前图像 | 635 张 | 1024 × 1024 | RGB，PNG |
| 4 | **主要使用** | Coast Train（D05） | Pelican Island、Little Dauphin Island | 42 张 | 40 张 2048 × 2048；2048 × 1760、2048 × 1728 各 1 张 | RGB，PNG；从原 NPZ 的 image 前三颜色通道导出 |
| 5 | 补充使用 | USGS Oregon 10 Islands（D02） | 俄勒冈近海 10 岛的正射镶嵌影像 | 8 幅 | 各图不同，见下表 | 3 幅 RGB、5 幅 RGBA，COG GeoTIFF |
| 6 | 补充使用 | Galápagos Santa Cruz（D04） | Coastline、CoastlineCharles 两幅海岸正射图 | 2 幅 | 60518 × 52761；33348 × 12383 | RGBA，GeoTIFF |

前四项的 1,663 张图块与后两项的 10 幅大图属于不同数据形态。后两项尚未裁为统一规格的训练图块。

## 2. 子集范围与标签情况

### 1）NWPU-RESISC45

- 只选 island 类 700 张，没有将其他 44 类纳入本次海岛子集。
- 700 张均为 256 × 256 的 RGB 图像，保留镜像中的原始图像字节，未缩放或重编码。
- 标签为 island 场景类别，不包含本项目所需的飞机或舰船水平框。
- 镜像 train / validation / test 仅作为下载来源记录，实验划分需按本项目方案确定。

### 2）OpenEarthMap

- Mahe 70 张、Tonga 70 张、Zanzibar 146 张，共 286 张。
- 本次同时取得 199 张配套分割标签：Mahe 49、Tonga 49、Zanzibar 101。
- 其余 87 张本地没有配套标签，不能将缺失标签视为“背景”。
- 分割标签与 RGB 输入分别统计，不把标签图计入 286 张图像。

### 3）xBD / xView2

- Lower Puna 291 张、Palu 196 张、Sunda 148 张，共 635 张灾前 RGB 图像。
- 两个公开镜像来源合并后，按场景 ID 和 SHA-256 去重。
- 本次只下载上述灾前 PNG，没有下载对应灾后图和建筑标签，不能描述为已有 635 组灾前/灾后配对。
- 旧下载记录仅涉及最初 Palu 的 155 张；635 张总数以本地最终合并校验记录为准。

### 4）Coast Train

- 两个岛屿的采集时相：Pelican Island 为 2018 年 9 月、11 月；Little Dauphin Island 为 2018 年 12 月、2019 年 3 月。
- 四个时相分别为 14、12、8、8 张，共 42 张；选中样本实际来自 Orthophoto_9_001 分包。
- 原 NPZ 的 image 为四通道数组，本次只取前三个 RGB 通道导出 PNG；未缩放、未拉伸、未增强，与原前三通道逐像素一致。
- 原包中的 label、doodles 等字段不作为真实彩色照片。
- 本次实际文件以 2048 像素规格为主，与发布资料中概述的 1024 像素切片不同，以本地实读尺寸为准。

### 5）USGS Oregon：逐幅尺寸

8 幅正射镶嵌图覆盖 10 个岛屿，部分相邻岛屿由同一幅镶嵌图覆盖。

| 文件 | 宽 × 高（像素） | 通道 |
|---|---:|---|
| GoatIsland123_Orthomosaic_COG.tif | 24793 × 30836 | RGBA |
| HuntersIsland071_Orthomosaic_COG.tif | 19753 × 25551 | RGBA |
| MyersCreekRocks074_Orthomosaic_COG.tif | 14523 × 17500 | RGB |
| NorthCrookPointRock076_Orthomosaic_COG.tif | 8020 × 11671 | RGBA |
| SaddleRock079_Orthomosaic_COG.tif | 17736 × 25128 | RGBA |
| UnnamedIsland106_Orthomosaic_COG.tif | 16043 × 9196 | RGB |
| UnnamedIsland73_Orthomosaic_COG.tif | 10298 × 10263 | RGB |
| WhalesheadCove109_Orthomosaic_COG.tif | 23211 × 32940 | RGBA |

本次未下载 DSM、点云和原始斜视照片。部分官方文件名记录含前导零，实际下载对象为 UnnamedIsland73_Orthomosaic_COG.tif。

### 6）Galápagos：逐幅尺寸

| 文件 | 宽 × 高（像素） | 通道 |
|---|---:|---|
| Coastline.tif | 60518 × 52761 | RGBA |
| CoastlineCharles.tif | 33348 × 12383 | RGBA |

两幅图的 Alpha 通道表示透明度/有效区域，不是第四个光谱波段。USGS 中的 RGBA 影像同理。模型颜色输入取 RGB，按需利用 Alpha 排除无效区域。

## 3. 像素尺寸与地面分辨率

像素尺寸记录图像的宽和高。地面像元大小另行记录，不能由 256、1024 或 2048 等尺寸直接推算。

| 数据集 | 本次可确认的地面像元信息 |
|---|---|
| NWPU-RESISC45 | 没有逐图统一核实 GSD，不填写统一米/像素数值 |
| OpenEarthMap | Mahe 70 张为 0.3 米/像素；Zanzibar 76 张约 0.3 米/像素、70 张为 0.5 米/像素；Tonga 70 张的 GeoTIFF 使用经纬度，像元尺度约 2.818314 × 10⁻⁶ 度，不能直接当成米 |
| xBD | 未独立核实最终 PNG 的统一 GSD；TACO 的 pre_gsd_m 为来源元数据字段，不直接视为最终全色融合 PNG 的独立测量值 |
| Coast Train | 42 条对应发布 CSV 的 px_m 均为 0.05 米，即 5 厘米/像素 |
| USGS Oregon | 发布元数据的名义分辨率约 1.5 厘米/像素；各 GeoTIFF 的坐标系及像元单位需逐幅解释 |
| Galápagos | 两幅 GeoTIFF 像元大小均约 0.0278954 米，即 2.79 厘米/像素；不代表绝对定位精度 |

## 4. 来源与许可记录

以下许可名称按本次下载时保存的来源记录整理，来源页保留原始发布与引用信息。

| 数据集 | 原始发布来源 | 本次获取渠道 | 许可记录 |
|---|---|---|---|
| NWPU-RESISC45 | [作者数据集页](https://gcheng-nwpu.github.io/#Datasets) | [timm/resisc45 公开镜像](https://huggingface.co/datasets/timm/resisc45) | CC BY-NC 4.0；镜像卡的 unknown 不替代作者许可 |
| OpenEarthMap | [Zenodo 7223446](https://zenodo.org/records/7223446) | 官方 OpenEarthMap.zip 中的三岛区成员 | CC BY 4.0，保留分区域来源署名 |
| xBD / xView2 | [xView2 数据集页](https://xview2.org/dataset) | [aryananand/xBD](https://huggingface.co/datasets/aryananand/xBD) 与 [isp-uv-es/xview2-taco](https://huggingface.co/datasets/isp-uv-es/xview2-taco) | CC BY-NC-SA 4.0，保留 xBD 与原始影像来源 |
| Coast Train | [官方数据说明](https://coasttrain.github.io/CoastTrain/docs/Version%201:%20March%202022/data/) | USGS 官方 Orthophoto 分包内所选岛屿成员 | USGS 公共领域目录记录，保留原图来源及引用 |
| USGS Oregon | [DOI：10.5066/P14F6BIP](https://doi.org/10.5066/P14F6BIP) | USGS 官方正射 COG | 公共领域 / CC0 |
| Galápagos | [Zenodo 7924523](https://zenodo.org/records/7924523) | 官方发布包内两幅 Orthophotos | CC BY 4.0 |

NWPU 参考文献：Gong Cheng, Junwei Han, Xiaoqiang Lu. Remote Sensing Image Scene Classification: Benchmark and State of the Art. Proceedings of the IEEE, 105(10):1865–1883, 2017. DOI：[10.1109/JPROC.2017.2675998](https://doi.org/10.1109/JPROC.2017.2675998)。

## 5. 当前项目使用安排

- 主要使用第 1—4 项构建公开海岛 RGB 输入，开展样本扩容及相应对照；第 5—6 项保留为补充场景来源。
- 正射大图采用窗口裁片；实验先按岛屿、原图或场景分组划分，再裁片，保留来源与处理记录。
- 公开图像不自动构成 COSSIM 同视点清晰 A / 退化 B 配对。保真复原评价仍需独立核对图组；飞机、舰船识别所需水平框由项目另行确认。
- 本页的数量与参数来自本地 source、README、validation、最终下载校验汇总及 2026-11-12 的文件头核对；来源容器和下载字节段不计入图像数量，也不上传到仓库。
