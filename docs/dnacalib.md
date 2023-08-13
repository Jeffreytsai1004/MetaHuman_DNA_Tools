# DNACalib
该库用于对 DNA 文件进行修改。 
它是用 C++ 编写的，并且还有一个 Python 包装器。 
SWIG 库用于生成 Python 的绑定。 DNACalib 可以在命令行或 Maya 中使用。 
提供了适用于 Windows 和 Linux 的二进制文件。 
如果您使用不同的架构和/或平台，则必须构建 DNACalib。

## DNACalib 文件夹结构
- [`DNACalib`](/dnacalib/DNACalib) - 包含 DNACalib 的 C++ 源代码及其依赖项。 有一个图书馆读取和写入 DNA 文件，以及一些其他实用程序库。
- [`PyDNACalib`](/dnacalib/PyDNACalib) - 包含用于生成 DNACalib 的 Python 包装器的源代码。
- [`PyDNA`](/dnacalib/PyDNA) - 包含用于生成 DNA 库的 Python 包装器的源代码，位于DNACalib 文件夹包含 C++ 源代码。
- [`SPyUS`](/dnacalib/SPyUS) - 包含 PyDNACalib 和 PyDNA 使用的一些常见 SWIG 接口文件。
- [`CMakeModulesExtra`](/dnacalib/CMakeModulesExtra) - 包含一些在整个过程中使用的常见 CMake 函数项目，采用 C++ 和 Python 包装器。

## 用法

例如，要更改中性关节的旋转值，请使用
[`SetNeutralJointRotationsCommand`](/dnacalib/DNACalib/include/dnacalib/commands/SetNeutralJointRotationsCommand.h).

下面是读取 DNA，将所有中性关节的旋转值更改为 `{1, 2, 3}`, 并用这些新值覆盖 DNA 文件。

```

// Create DNA reader
auto inOutStream = dnac::makeScoped<dnac::FileStream>("example.dna",
                                                      dnac::FileStream::AccessMode::ReadWrite,
                                                      dnac::FileStream::OpenMode::Binary);
auto reader = dnac::makeScoped<dnac::BinaryStreamReader>(inOutStream.get());
reader->read();

// Check if an error occurred while reading DNA file
if (!dnac::Status::isOk()) {
    // handle reader error
}

// Create DNACalib reader in order to edit DNA
auto dnaReader = dnac::makeScoped<dnac::DNACalibDNAReader>(reader.get());

std::vector<dnac::Vector3> rotations{dnaReader->getJointCount(), {1.0f, 2.0f, 3.0f}};

// Create command instance
dnac::SetNeutralJointRotationsCommand cmd{dnac::ConstArrayView<dnac::Vector3>{rotations}};

// Execute command
cmd.run(dnaReader.get());

// Write DNA file
auto writer = dnac::makeScoped<dnac::BinaryStreamWriter>(inOutStream.get());
writer->setFrom(dnaReader.get());
writer->write();

// Check if an error occurred while writing DNA file
if (!dnac::Status::isOk()) {
    // handle writer error
}
```

## 例子

### C++
C++ 库的使用示例可以在[此处](/dnacalib/DNACalib/examples) 找到。

这些都是：
- [链接多个命令](/dnacalib/DNACalib/examples/CommandSequence.cpp)
- [重命名混合形状](/dnacalib/DNACalib/examples/SingleCommand.cpp)

### Python
使用 Python 库的示例是[此处](/examples)。

这些都是：
- [展示一些命令](/examples/dnacalib_demo.py)
- [重命名关节](/examples/dnacalib_rename_joint_demo.py)
- [从头开始创建一个小 DNA](/examples/dna_demo.py)
- [通过提取特定 LOD 从现有 DNA 中创建新 DNA](/examples/dnacalib_lod_demo.py)
- [删除关节](/examples/dnacalib_remove_joint.py)
- [清除混合形状数据](/examples/dnacalib_clear_blend_shapes.py)
- [从中性网格中减去值](/examples/dnacalib_neutral_mesh_subtract.py)


## Build
[provided](/lib)适用于 64 位 Windows 和 Linux 的预构建二进制文件。
如果您使用不同的架构和/或平台，则必须构建 DNACalib。

先决条件：
- [CMake](https://cmake.org/download/) 至少版本 3.14
- [SWIG](https://www.swig.org/download.html) 至少版本 4.0.0
- [Python](https://www.python.org/downloads/) 要指定要使用的 python3 的确切版本，请设置 CMake 变量
`PYTHON3_EXACT_VERSION`。 例如，要使用 Maya 2022 中的库，请使用版本 3.7。

使用 CMake 生成构建所需的构建脚本，例如 通过执行以下命令
[`dna_calibration/dnacalib/`](/dnacalib) directory:

```
mkdir build
cd build
cmake ..
```
随后，开始构建过程：
```
cmake --build
```
