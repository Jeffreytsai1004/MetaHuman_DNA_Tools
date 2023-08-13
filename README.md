# MetaHuman DNA Tools
MetaHuman DNA Tools 是用于处理 MetaHuman DNA 的工具集。 它基于 [MetaHuman DNA Calibration 1.0.3] [MetaHuman DNA Calibration 1.0.3](https://github.com/EpicGames/MetaHuman-DNA-Calibration/tree/1.0.3).  

# 文档
[数字人空间增强版MetaHuman DNA查看器保姆级安装和使用教程](https://www.bilibili.com/read/cv25377931)

＃ 新功能
## DNAViewer
- DNA Viewer 的 Z 向上。
- DNA Viewer 的默认文件路径。
- 快速选择或取消选择所有 LOD。

# 安装要求
使用之前需要安装 python 包 `scipy`。

- 找到 **maya.exe** 的路径。
- 转到 Windows cmd 中的路径。
- 然后使用 mayapy.exe 安装 python 包 scipy。

```
mayapy.exe -m pip install scipy  
```


# MetaHuman DNA Calibration
MetaHuman DNA Calibration 是一组用于处理 MetaHuman DNA 文件的工具，捆绑在一个软件包中。
DNA 是 [MetaHuman](https://www.unrealengine.com/en-US/metahuman) 的一个组成部分。
DNA 文件是使用 [MetaHuman Creator](https://meta human.unrealengine.com/) 创建并使用
[Quixel Bridge](https://docs.meta human.unrealengine.com/en-US/downloading-metahumans-with-quixel-bridge/)。

MetaHuman DNA Calibration 是一组用于处理 MetaHuman DNA 文件的工具，捆绑在一个软件包中。 我们希望分享此代码来帮助用户自定义 DNA 文件，以便他们可以更好地将他们创建的角色融入到他们的游戏和体验中。
位于此地址的 GitHub 存储库中提供了 MetaHuman DNA 校准工具。


＃ 概述
有关如何组织存储库的说明，请[单击此处](docs/repository_organization.md)。

MetaHuman DNA 校准存储库包含两个不同的工具：
- [DNACalib](docs/dnacalib.md)（及其依赖项）
- [DNAViewer](docs/dna_viewer.md)


## 所需知识
要使用这些工具，您应该熟悉：
- Rigging in Maya
- Python

## 可选知识
- C++（对于 [DNACalib](docs/dnacalib.md) 及其 [API](docs/dnacalib_api.md)）


## DNA 校准
[DNACalib](docs/dnacalib.md) 及其 [API](docs/dnacalib_api.md) 用于检查和修改 DNA 文件。 使用 [DNACalib](docs/dnacalib.md)，您可以在 DNA 文件中进行以下更改：
- 重命名关节、网格、混合形状和/或动画贴图。
- 删除关节、网格和/或关节动画。
- 旋转、缩放和平移装备。
- 删除 LOD。
- 更改中性关节位置、中性网格位置和混合形状增量值。
- 修剪混合形状。
- 删除所有混合形状数据。


## 外部软件依赖项
DNACalib 的 Python 包装器是针对 Python 3.7 编译的。 适用于 Windows 和 Linux（均为 64 位）的预编译二进制文件是存储库的一部分。
如果您使用不同版本的Python，则必须重新编译它。 任何 Python 3 版本都应该没问题。
如果用户有不同的平台或体系结构，则必须编译库及其依赖项。

**重要的**
DNA 文件存储为 [LFS（大文件存储）](https://git-lfs.github.com/) 文件。 如果满足以下条件，它们将与其余代码一起下载
git-lfs 已安装并配置为使用。 如果您不使用 git-lfs，则必须手动下载 DNA 文件。

其他信息可以在[此处](docs/faq.md#fix--runtimeerror--error-loading-dna--dna-signature-mismatched-expected-dna-got-ver-)找到

**警告：**
不支持 Python 2。

DNACalib 可以作为 C++ 库在 C++ 项目中使用。

DNACalib Python 包装器可在 Python 3.7、“mayapy”（Maya 的 Python 解释器）或 Maya 2022 中使用。


## DNA查看器
使用 DNAViewer，您可以：
- 为 Maya 创建功能装备。
- 导出 FBX 文件。
- 读取 DNA 文件的内部部分。

DNAViewer 可以在 `mayapy`（Maya 的 Python 解释器）或 Maya 2022 中使用，但 [将更改从 Maya 场景传播到 dna](/examples/dna_viewer_grab_changes_from_scene_and_propagate_to_dna.py) 除外，它只能在 Maya 中使用。

＃ 例子
提供了几个 Python 示例供参考，可以在 **examples'** 文件夹中找到：
- [展示一些命令](/examples/dnacalib_demo.py)
- [重命名关节](/examples/dnacalib_rename_joint_demo.py)
- [从头开始创建一个小 DNA](/examples/dna_demo.py)
- [通过提取特定 LOD 从现有 DNA 中创建新 DNA](/examples/dnacalib_lod_demo.py)
- [删除关节](/examples/dnacalib_remove_joint.py)
- [清除混合形状数据](/examples/dnacalib_clear_blend_shapes.py)
- [从中性网格中减去值](/examples/dnacalib_neutral_mesh_subtract.py)
- [Maya 中的简单 UI](examples/dna_viewer_run_in_maya.py) 和一些 [文档](docs/dna_viewer.md#usage-in-maya)
- [生成装备并导出每个 LOD 的 FBX](examples/dna_viewer_demo.py)
- [将更改从 Maya 场景传播到 dna](/examples/dna_viewer_grab_changes_from_scene_and_propagate_to_dna.py)

## DNA 文件示例
提供[两个演示 DNA 文件](data/dna)，以便更轻松地测试该工具。 使用 [MetaHumanCreator](https://www.unrealengine.com/en-US/metahuman) 生成的任何 DNA
应该管用。

# 注释
如果用户在 Maya 2022 中运行示例，则应更改“ROOT_DIR”的值并且必须使用绝对路径，
例如。 Windows 中为“c:/dna_calibration”，Linux 中为“/home/user/dna_calibration”。 重要提示：使用“/”（正斜杠），Maya 在路径中使用正斜杠。

有关其他规范，请参阅[常见问题解答指南](docs/faq.md)。

＃ 执照
MetaHuman DNA Calibration 已获得[许可证](LICENSE) 发布。
