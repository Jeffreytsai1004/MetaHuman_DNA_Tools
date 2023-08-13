[`dna_viewer`](/dna_viewer) 包含从 DNA 文件读取和在 Maya 中创建功能装备所需的所有类。
它的组织方式允许每个选项都是可配置的，因此您可以轻松获得您想要的确切结果。

## 例子
- [根据 LOD 生成装备并导出 FBX](/examples/dna_viewer_demo.py)
- [将更改从 Maya 场景传播到 dna](/examples/dna_viewer_grab_changes_from_scene_and_propagate_to_dna.py)
- [简单用户界面](/examples/dna_viewer_run_in_maya.py)


## 代码中的用法
那里有两个 [APIs](docs/dna_viewer_api.md):
  - [assemble](docs/dna_viewer_api_rig_assembly.md)
  - [mesh](docs/dna_viewer_api_mesh_utilities.md)

这些的用法可以在 [dna_viewer_demo.py](/examples/dna_viewer_demo.py).

## 在Maya中的用法
Maya 中的用法说明 [here](dna_viewer_maya.md)


## 文件夹结构

- [builder](/dna_viewer/builder) - 包含构建器类，用于轻松添加配置选项并构建场景、角色、网格等。
- [config](/dna_viewer/config) - 包含表示配置选项的类。 这些文件用于微调选项。
- [const](/dna_viewer/const) - 包含项目中使用的常量文件。
- [model](/dna_viewer/model) - 包含项目中使用的数据类。
- [reader](/dna_viewer/reader) - 包含用于读取 DNA 文件内容的类。
- [ui](/dna_viewer/ui) - 包含 Maya UI 所需的类。
- [util](/dna_viewer/util) - 主要包含 Maya 方法调用的包装类。

## 如何运行

一般流程如下：

![image](img/flow_general.png)

场景构建流程如下：

![image](img/flow_scene_build.png)

Blender构建过程的流程如下：

![image](img/flow_character_build.png)

Legend:
- <span style="color:blue">blue: builder-related</span>.
- <span style="color:green">green: config-related</span>.
- <span style="color:brown">brown: model-related</span>.
- <span style="color:purple">purple: reader-related</span>.
