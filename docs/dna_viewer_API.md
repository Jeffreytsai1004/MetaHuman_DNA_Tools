# 环境设置

为了能够从 dna_viewer 导入，需要设置环境。 这是通过将此代码添加到下面提到的任何示例的开头：

```
from sys import path as syspath, platform
from os import environ, path as ospath

ROOT_DIR = fr"{ospath.dirname(ospath.abspath(__file__))}/..".replace("\\", "/") # if you use Maya, use an absolute path instead
ROOT_LIB_DIR = fr"{ROOT_DIR}/lib"
if platform == "win32":
    LIB_DIR = f"{ROOT_LIB_DIR}/windows"
elif platform == "linux":
    LIB_DIR = f"{ROOT_LIB_DIR}/linux"
else:
    raise OSError("OS not supported, please compile dependencies and add value to LIB_DIR")


if "MAYA_PLUG_IN_PATH" in environ:
    separator = ":" if platform == "linux" else ";"
    environ["MAYA_PLUG_IN_PATH"] = separator.join([environ["MAYA_PLUG_IN_PATH"], LIB_DIR])    
else:
    environ["MAYA_PLUG_IN_PATH"] = LIB_DIR

syspath.append(ROOT_DIR)
syspath.append(LIB_DIR)
```

从 Maya 运行此程序时，应将“ROOT_DIR”设置为存储库根目录的绝对路径。

# DNA

## 加载 DNA ([`load_dna`](../dna_viewer/reader/dna.py#L28))

加载 DNA 并返回 [`DNA`](../dna_viewer/model/dna.py#L40) 对象。

```
from dna_viewer import get_dna

dna_ada = load_dna(DNA_PATH_ADA)
dna_taro = load_dna(DNA_PATH_TARO)
```

这使用以下参数：
- `dna_path: str` - 应使用的 DNA 文件的路径。

## 网格实用程序

Mesh Utilities API 说明位于[此处](/docs/dna_viewer_api_mesh_utilities.md)。

## Rig Assembly

Rig Assembly API 说明位于[此处](/docs/dna_viewer_api_rig_ assembly.md)。
