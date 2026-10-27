# IPRR connector assembly datasets

Public robot demonstration datasets for **IPRR: A VLA-Based View-Projection Residual Method for Precision Assembly**.

| Dataset | Role in the paper | Episodes | Frames | Recording rate |
| --- | --- | ---: | ---: | ---: |
| `so101_connector_assembly_dual_v1` | Training demonstration pool | 98 | 31,342 | 15 Hz |
| `so101_connector_random96_v2` | Separately recorded test set | 96 | 30,856 | 15 Hz |

## Download

Download the complete datasets from [Release v1.0.0](https://github.com/joker2152/iprr-connector-datasets/releases/tag/v1.0.0):

- [98 training demonstrations](https://github.com/joker2152/iprr-connector-datasets/releases/download/v1.0.0/so101_connector_assembly_dual_v1.zip)
- [96 test demonstrations](https://github.com/joker2152/iprr-connector-datasets/releases/download/v1.0.0/so101_connector_random96_v2.zip)

Each archive contains the original dataset directory, including `data/` Parquet files, `meta/` information, and `videos/` for the external and wrist cameras. Data binaries are distributed as GitHub Release assets; cloning this repository downloads documentation and metadata.

## Format and use

The source datasets use the LeRobot v3.0 directory format and record an SO-101 arm performing HARTING connector assembly. The stored action and observation state contain six joint coordinates including the gripper; see the unmodified dataset feature metadata in `metadata/` for exact schemas.

Extract each ZIP into your desired data directory. Multiple episodes share chunked Parquet and video files, so file count is different from episode count. Keep the complete directory structure.

The paper uses the 98 demonstrations to train the base policy. Residual fitting and selection use 58 fitting and 20 validation episodes from that pool; the other 20 episodes are excluded from this residual fitting/selection round. Episode identifiers are provided in [`metadata/paper_splits.json`](metadata/paper_splits.json).

The 96 demonstrations are used as the paper's test set. Its original LeRobot metadata uses the generic split name `train` (`0:96`); this metadata field does **not** change its test role in the paper. The archived metadata and data content are preserved.

This release contains the two demonstration datasets. Residual model checkpoints, cached visual features, offline predictions, public simulation benchmark data, and physical-trial logs are separate research materials and are not included in these dataset archives.

## License

Released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). When using the data, attribute **joker2152, IPRR connector assembly datasets (2026)** and link to this repository. No manuscript DOI is specified here because it has not been provided for this release.

## 中文说明

本仓库公开 IPRR 论文使用的 98 条训练示范和 96 条单独录制的测试示范。完整双视角视频、逐帧 Parquet 数据和原始元数据位于上方 GitHub Releases 下载链接中。下载后保持原目录结构；视频与数据采用分块存储，文件数不等于回合数。测试集原始格式中的 `train` 划分名称予以保留，论文实验中仍作为测试集使用。数据按 CC BY 4.0 开放。
