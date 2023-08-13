# Mesh 工具

以下方法的目的是提供：
- 一种从给定 DNA 文件路径构建网格的简单机制
- 返回并打印有关 DNA 文件中包含的网格的信息

## Importing

```
from dna_viewer import build_meshes, create_build_options, #get_mesh_index, get_mesh_lods, get_mesh_names, print_meshes, print_mesh_indices_containing_string
```

```
DNA_PATH_ADA = f"{ROOT_DIR}/data/dna/Ada.dna"
DNA_PATH_TARO = f"{ROOT_DIR}/data/dna/Taro.dna"
```

## 创建构建选项 ([`create_build_options`](../dna_viewer/util/mesh.py#L31))
用于创建将在网格构建过程中使用的配置对象。

```
build_options = create_build_options(
    add_joints=True,
    add_normals=False,
    add_blend_shapes=False,
    add_skin=False,
    add_ctrl_attributes_on_root_joint=False,
    add_animated_map_attributes_on_root_joint=False
)
```

这使用以下参数：
- `add_joints: bool` - 表示是否应添加关节的标志，默认为“False”。
- `add_normals: bool` - 表示是否应添加 DNA 文件中的法线的标志，默认为“False”。
- `add_blend_shapes: bool` - 表示是否应添加混合形状的标志，默认为“False”。
- `add_skin: bool` - 表示是否应添加皮肤簇的标志，默认为“False”。
- `add_ctrl_attributes_on_root_joint: bool` - 表示是否应将控制属性添加到根关节的标志
作为属性，默认为“False”。 它们用作引擎中 Rig Logic 输入的动画曲线。
- `add_animated_map_attributes_on_root_joint: bool` - 表示动画地图属性是否应添加到的标志
根关节作为属性，默认为“False”。 它们用作引擎中动画地图的动画曲线。

**重要**：某些标志值组合可能会导致装备无法使用或禁用某些功能！



## 构建网格 ([`build_meshes`](../dna_viewer/util/mesh.py#L49))

用于在没有 Rig Logic 的情况下构建装备元素（关节、网格、混合形状和蒙皮簇）。
它返回已添加到场景中的网格体的长名称。

```
mesh_names = build_meshes(
    dna=dna_ada,
    options=build_options,
    group_by_lod=True,
    lod_list=[0, 1],
    mesh_list=[38],
    create_new_scene=True
)
```


这使用以下参数：
- `dna: DNA` - 通过 `load_dna` 获得的 DNA 实例。
- `lod_list: List[int]` - 用于构建所有网格体的 LOD 列表。
- `mesh_list: List[int]` - 要构建的网格索引列表。
- `group_by_lod: bool` - 表示构建的网格是否应添加到场景中的 MetaHuman 组层次结构的标志，默认为 `False`。 如果值为“False”，所有创建的装备元素都将添加到场景的根中。
- `选项：BuildOptions` - 设置[构建选项](../dna_viewer/config/character.py#L32)。
- `create_new_scene: bool` - 如果为`True`，将在创建装备元素之前打开一个新场景。 默认为“假”。

如果未设置 `lod_list` 和 `mesh_list` ，则将构建所有网格。

该方法也可以仅使用 DNA 文件路径来调用：

```
mesh_names = build_meshes(dna=dna_ada)
```

默认添加 DNA 文件中的所有网格。


## 获取网格名称和 LOD 中包含的给定字符串的网格索引 ([`get_mesh_index`](../dna_viewer/util/mesh.py#L120))

返回包含搜索字符串的网格的网格索引。 如果找到多个匹配项，则返回第一个匹配项。

```
mesh_id = get_mesh_index("eye", 0, dna_ada)
```

这使用以下参数：
- `mesh_name: str` - 用于获取包含它的网格名称的网格索引的搜索字符串。
- `lod: int` - 搜索网格的 LOD。
- `dna: DNA` - 通过 `load_dna` 获得的 DNA 实例。
出现异常。

### 获取所有网格名称的列表 ([`get_mesh_names`](../dna_viewer/util/mesh.py#L13)))

返回 DNA 中所有网格名称的列表。

```
mesh_names = get_mesh_names(dna_ada)
```

这使用以下参数：
- `dna: DNA` - 通过 `load_dna` 获得的 DNA 实例。
出现异常。

### 获取按 LOD 组织的网格索引列表 ([`get_mesh_lods`](../dna_viewer/util/mesh.py#L17))

返回按 LOD 编号分组的网格索引列表。

```
mesh_indices_by_lod = get_mesh_lods(dna_ada)
```

这使用以下参数：
- `dna: DNA` - 通过 `load_dna` 获得的 DNA 实例。

### 打印所有网格 ([`print_meshes`](../dna_viewer/util/mesh_helper.py#L8))

打印按 LOD 分组的网格索引和名称。

```
print_meshes(dna_ada)
```

这使用以下参数：
- `dna: DNA` - 通过 `load_dna` 获得的 DNA 实例。

### 打印名称包含搜索字符串的所有网格索引 ([`print_mesh_indices_containing_string`](../dna_viewer/util/mesh_helper.py#L18))

打印名称中包含给定 LOD 中给定搜索字符串的所有网格及其索引。

```
print_mesh_indices_containing_string("eye", 3, dna_ada)
```

### 例子

**重要**：在运行此示例之前需要执行上面提供的设置代码。

```
from dna_viewer import build_meshes, create_build_options
from dna_viewer import print_meshes
from dna_viewer import load_dna

# Sets DNA file path
DNA_PATH_ADA = f"{ROOT_DIR}/data/dna/Ada.dna"
# Prints the mesh ids and names grouped by lods
dna_ada = load_dna(DNA_PATH_ADA)
print_meshes(dna_ada)

# Starts the mesh build process with all the default values
build_meshes(dna_path=dna_ada)

# Creates the options to be passed in `build_meshes`
build_options = create_build_options(
    add_joints=True,
    add_normals=True,
    add_blend_shapes=True,
    add_skin=True,
    add_ctrl_attributes_on_root_joint=True,
    add_animated_map_attributes_on_root_joint=True
)

# Starts the mesh building process with the provided parameters
# In this case it will create every mesh contained in LODs 0 and 1,
# it also adds the mesh with the mesh index value of 38
build_meshes(
    dna=dna_ada,
    options=build_options,
    group_by_lod=True,
    lod_list=[0, 1],
    mesh_list=[38],
    create_new_scene=True
)
```
