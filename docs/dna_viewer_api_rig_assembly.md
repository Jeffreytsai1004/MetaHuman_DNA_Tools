# Rig Assembly 绑定装配

装配 API 用于从给定的 DNA 文件路径轻松装配 Maya 场景中的角色装备。

## Importing 导入

```
from dna_viewer import assemble_rig
```

这使用以下参数：
- `dna: DNA` - 通过 `load_dna` 获得的 DNA 实例。
- `gui_path: str` - GUI 文件路径。
- `analog_gui_path: str` - 模拟 GUI 文件路径。
- `aas_path: str` - 附加的汇编脚本路径。
- `aas_fn: str` - 应从附加汇编脚本调用的方法名称。
- `with_attributes_on_root_joint: bool` - 表示是否应在根关节上添加属性的标志，默认为“False”。
- `with_key_frames: bool` - 表示是否应添加关键帧的标志，默认为 `False`

## 例子

**重要**：在运行此示例之前需要执行上面提供的设置代码。

```
from dna_viewer import assemble_rig, load_dna

# Sets the values that will used
DNA_PATH_ADA = f"{ROOT_DIR}/da/dna/Ada.dna"
dna_ada = load_dna(DNA_PATH_ADA)
GUI_PATH = f"{ROOT_DIR}/data/gui.ma"
ANALOG_GUI_PATH = f"{ROOT_DIR}/data/analog_gui.ma"
AAS_PATH = f"{ROOT_DIR}/data/after_assembly_script.py"

# Creates the rig
assemble_rig(
    dna=dna_ada,
    gui_path=GUI_PATH,
    analog_gui_path=ANALOG_GUI_PATH,
    aas_path=AAS_PATH,
    aas_fn="run_after_assemble"
)
```
