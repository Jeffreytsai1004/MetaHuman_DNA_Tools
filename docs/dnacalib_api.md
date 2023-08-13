# API 概述
DNA 修改是通过可用命令完成的。 每个命令都实现 `run(DNACalibDNAReader* output)` 方法
修改通过其参数指定的 DNA。 配置`run()`中发生的修改，参数
可以通过构造函数或特定的 setter 方法传递。
以下文档适用于 C++。 目前，还没有 Python 文档。

所有可用命令的列表：

## 删除 DNA 某些部分的命令：

- [`RemoveJointAnimationCommand`](/dnacalib/DNACalib/include/dnacalib/commands/RemoveJointAnimationCommand.h) 删除具有来自 DNA 的给定索引的关节动画。

- [`RemoveJointCommand`](/dnacalib/DNACalib/include/dnacalib/commands/RemoveJointCommand.h) 删除给定的关节DNA 的索引。

- [`RemoveMeshCommand`](/dnacalib/DNACalib/include/dnacalib/commands/RemoveMeshCommand.h) 删除具有给定索引的网格来自DNA。

- [`ClearBlendShapesCommand`](/dnacalib/DNACalib/include/dnacalib/commands/ClearBlendShapesCommand.h) 清除所有混合形状数据来自DNA。

## 重命名 DNA 某些部分的命令：

- [`RenameAnimatedMapCommand`](/dnacalib/DNACalib/include/dnacalib/commands/RenameAnimatedMapCommand.h) 重命名动画具有给定索引或先前名称的地图。

- [`RenameBlendShapeCommand`](/dnacalib/DNACalib/include/dnacalib/commands/RenameBlendShapeCommand.h) 重命名 BlendShape 具有给定索引或以前的名称。

- [`RenameJointCommand`](/dnacalib/DNACalib/include/dnacalib/commands/RenameJointCommand.h) 使用给定的名称重命名关节索引或以前的名称。

- [`RenameMeshCommand`](/dnacalib/DNACalib/include/dnacalib/commands/RenameMeshCommand.h) 使用给定索引重命名网格或以前的名字。

## 改变 DNA 的命令:

- [`RotateCommand`](/dnacalib/DNACalib/include/dnacalib/commands/RotateCommand.h) 旋转中性关节和顶点给定原点周围的位置。

- [`ScaleCommand`](/dnacalib/DNACalib/include/dnacalib/commands/ScaleCommand.h) 缩放中性关节、顶点位置、以及关节和混合形状增量的一个因子。 对于中性关节和关节增量，仅缩放平移属性。

- [`TranslateCommand`](/dnacalib/DNACalib/include/dnacalib/commands/TranslateCommand.h) 平移中性关节和顶点位置。

## 修改混合形状的命令：

   - [`SetBlendShapeTargetDeltasCommand`](/dnacalib/DNACalib/include/dnacalib/commands/SetBlendShapeTargetDeltasCommand.h)
  更改混合形状目标增量。

   - [`PruneBlendShapeTargetsCommand`](/dnacalib/DNACalib/include/dnacalib/commands/PruneBlendShapeTargetsCommand.h)
修剪低于或等于指定阈值的混合形状目标增量。

## 改变绑定姿势的命令：

   - [`SetNeutralJointRotationsCommand`](/dnacalib/DNACalib/include/dnacalib/commands/SetNeutralJointRotationsCommand.h)将新的旋转值设置为中性关节。

   - [`SetNeutralJointTranslationsCommand`](/dnacalib/DNACalib/include/dnacalib/commands/SetNeutralJointTranslationsCommand.h)将新的平移值设置为中性关节。

   - [`SetVertexPositionsCommand`](/dnacalib/DNACalib/include/dnacalib/commands/SetVertexPositionsCommand.h) 更改顶点位置值。

## 执行有用计算或提供附加功能的命令：

   - [`SetLODsCommand`](/dnacalib/DNACalib/include/dnacalib/commands/SetLODsCommand.h) 过滤 DNA，使其仅包含指定 LOD 的数据。

   - [`CalculateMeshLowerLODsCommand`](/dnacalib/DNACalib/include/dnacalib/commands/CalculateMeshLowerLODsCommand.h)重新计算指定网格体的较低 LOD 网格体的顶点位置。

   - [`CommandSequence`](/dnacalib/DNACalib/include/dnacalib/commands/CommandSequence.h) 在指定的 DNA 上运行一系列命令。

每个可用命令及其方法的更详细描述可以在[`DNACalib/include/dnacalib/commands`](/dnacalib/DNACalib/include/dnacalib/commands/)。
