# 常见问题 (FAQ)

## 修复“运行时错误：加载 DNA 时出错：DNA 签名不匹配，预期 DNA，有版本吗？”

为了解决这个问题，您应该安装[git-lfs](https://git-lfs.github.com/)，并再次克隆存储库。
DNA 文件将被正确下载。
如果无法安装 git-lfs，可以手动下载 DNA 文件。


## 如何分发 Maya 场景？

如果您的发行版中包含以下内容，您的场景应该可以开箱即用：
- 场景文件（`.mb` 文件）
- DNA（`.dna` 文件）
- 工作区（`workspace.mel` 文件）

所有这些文件需要一起分发。 如果这些文件未捆绑，并且您在 Maya 中使用装备时遇到一些问题，尝试以下步骤：

### 如何共享生成的文件？
如果要将生成的 Maya 场景分发给其他用户，则必须将“.dna”文件和“workspace.mel”与场景一起分发。

### 如何打开生成的场景？
在加载生成的场景之前，请执行以下步骤：
- 从主菜单中，转到“文件”>“设置项目”。
- 选择“workspace.mel”
- 设置包含文件夹（包含生成的 Maya 场景、“.dna”文件和“workspace.mel”）。


### 如何更改 Maya 场景中的 DNA 路径？
如果你想改变场景中的DNA路径：
- 在“outliner”中，取消选择“**仅 DAG 对象**”：
   - ![图片](img/change_path_outliner_settings.png)
- 仍在大纲视图中，搜索“rl4”。 您将看到一个名称以“rl4Embedded_”开头的文件。 单击该文件将其选中。
   - ![图片](img/change_path_outliner.png)
- 在“属性编辑器”中，您将能够使用“Dna 文件路径”更改路径：
   - ![图片](img/change_path_node_path.png)
