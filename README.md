# 爱捣鼓的小水木的博客（测试版） :link: https://MyMaskKing.github.io/testblog 
### :page_facing_up: [2](https://MyMaskKing.github.io/testblog/tag.html) 
### :speech_balloon: 0 
### :hibiscus: 7950 
### :alarm_clock: 2025-04-15 09:56:45 
### Powered by :heart: [Gmeek](https://github.com/Meekdai/Gmeek)

## Gmeek增强版使用说明

Gmeek增强版基于[Gmeek](https://github.com/Meekdai/Gmeek)，增加了`issue-publisher.yml`工作流，实现了从本地Markdown文件自动同步到GitHub Issues并生成博客的功能。

### 主要功能增强

1. **本地Markdown自动同步**：修改`issues/*.md`文件后自动同步到GitHub Issues
2. **图片资源自动处理**：自动下载文章中的图片并转存到仓库，确保图片链接永久有效
3. **双向同步**：
   - 新增/修改`issues/*.md`文件 → 创建/更新对应的GitHub Issue
   - 删除`issues/*.md`文件 → 关闭对应的GitHub Issue
4. **智能处理**：
   - 支持中文文件名（自动解码路径中的转义序列）
   - 只处理当前提交中变更的文件
   - 自动验证文件存在性
5. **标签管理**：
   - 从Markdown文件中提取标签（`ISSUE_LABELS:`行）
   - 自动创建缺失的标签
   - 更新时保留原有标签，只添加新标签

### 使用方法

1. **设置工作目录**：
   - 将Git中的`issues/`目录链接到[StackEdit](https://stackedit.cn/)或其他Markdown编辑器
   - 确保仓库根目录中存在`issues`文件夹

2. **编写文章**：
   - 在`issues/`文件夹下创建`.md`文件
   - 文件名将作为Issue标题和博客文章标题
   - 可选：在文件第一行添加标签定义：`ISSUE_LABELS: 标签1, 标签2, 标签3`
   - 如果未指定标签，将使用默认标签"文档"

3. **提交更改**：
   - 将更改推送到GitHub仓库
   - 工作流会自动检测`issues/*.md`文件的变更并处理

4. **图片处理**：
   - 文章中的图片会被自动下载并存储在`assets/images/文章名称/`目录下
   - 图片链接会被自动更新为指向仓库中的图片
   - 支持外部http链接图片、GitHub图片和相对路径图片

5. **删除文章**：
   - 从`issues/`目录删除`.md`文件并提交
   - 对应的Issue会被自动关闭
   - 对应的图片资源也会被清理

### Markdown文件格式示例

```markdown
ISSUE_LABELS: 技术, 教程, 前端

# 我的文章标题

这是文章内容...

![图片描述](https://example.com/image.jpg)
```

### 工作流触发条件

当`issues/*.md`文件有任何变更(新增、修改、删除)时，工作流会自动触发。

更多信息请访问[Gmeek官方文档](https://github.com/Meekdai/Gmeek)。
