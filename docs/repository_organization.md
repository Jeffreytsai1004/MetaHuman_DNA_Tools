# 存储库组织

该存储库包含两个独立的组件：
1. **dnacalib C++ 库** - 用于操作 DNA 文件
2. **dna_viewer python 代码** - 用于在 Autodesk Maya 中可视化 DNA

# 文件夹结构

- [dnacalib](/dnacalib) - DNACalib 源代码
- [dna_viewer](/dna_viewer) - dna_viewer的源代码
- [示例](/examples) - 几个 Python 脚本，用于展示 dna_viewer 和 DNACalib 的 Python 包装器的基本用法
- [lib](/lib) - DNACalib、PyDNACalib 和 PyDNA 的预构建二进制文件
- [数据](/数据) - 所需的 DNA 和 Maya 场景
- [文档](/docs) - 文档


## DNA 校准
文档位于[此处](dnacalib.md)

## DNA查看器
文档位于[此处](dna_viewer.md)

## 例子
要运行 [DNAViewer 示例](/docs/dna_viewer.md#examples)，您必须安装 Maya 2022。
要运行 [DNACalib 示例](/docs/dnacalib.md#python)，您需要 Python3。

## Lib

[Lib 文件夹](/lib) 包含适用于 Windows 和 Linux 的 DNACalib 库的预构建二进制文件。 此外，还有一个 Maya 插件 RL4 也可用。

### Linux 位置
您必须为 [lib](lib/linux) 中的所有 **.so** 文件复制或创建符号链接：

```shell
sudo ln -s ~/dna_calibration/lib/linux/_py3dna.so /usr/lib/_py3dna.so

sudo ln -s ~/dna_calibration/lib/linux/libdnacalib.so /usr/lib/libdnacalib.so

sudo ln -s ~/dna_calibration/lib/linux/libdnacalib.so.6 /usr/lib/libdnacalib.so.6

sudo ln -s ~/dna_calibration/lib/linux/libembeddedRL4.so /usr/lib/embeddedRL4.mll

```

注意：将路径 `~/dna_calibration` 更改为 `dna_calibration` 所在位置。

## Data

[`数据文件夹`](/data) 包含示例 DNA 文件。 我们提供了两个 MetaHuman DNA 文件（Ada 和 Taro，我们的第一个预设）。

| Ada | Taro |
|---|---|
|![image](img/metahuman_008.png)| ![image](img/metahuman_010.png) |

此外，我们还添加了 [`gui`](/data/gui.ma) 和 [`analog_gui`](/data/analog_gui.ma) Maya 场景，这些场景在
玛雅场景组装。
此外，[`after_assemble_script.py`](/data/after_assemble_script.py) 用于组织场景中的对象和
连接控件。 理想的设置如下所示：

![image](img/aas.png)
