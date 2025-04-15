# 爱捣鼓的小水木的博客（测试版） :link: https://MyMaskKing.github.io/testblog 
### :page_facing_up: [2](https://MyMaskKing.github.io/testblog/tag.html) 
### :speech_balloon: 0 
### :hibiscus: 7950 
### :alarm_clock: 2025-04-15 09:56:45 
### Powered by :heart: [Gmeek](https://github.com/Meekdai/Gmeek)

## Gmeek增强版使用说明

Gmeek增强版是基于[原版Gmeek](https://github.com/Meekdai/Gmeek)的改进版本，通过GitHub Actions实现了本地Markdown文件与GitHub Issues的双向自动同步，大大简化了博客内容管理流程。

### 核心功能

- **本地Markdown与Issues双向同步**：将本地`issues/`目录中的Markdown文件自动同步为GitHub Issues
- **文件变更智能监控**：自动检测`issues/*.md`文件的新增、修改和删除
- **标签自动管理**：从Markdown文件中提取标签信息并自动应用到Issues

### 使用方法

#### 1. 基础设置

1. 克隆仓库到本地
2. 确保`.github/workflows/issue-publisher.yml`工作流文件存在
3. 在仓库根目录创建`issues`文件夹(如不存在)

#### 2. 创建文章

1. 在`issues/`目录下创建Markdown文件(如`my-first-post.md`)
2. 文件名将自动成为Issue的标题
3. 在文件开头可以定义标签：
   ```
   ISSUE_LABELS: 技术, 教程, 心得
   
   这里开始是文章正文内容...
   ```
4. 保存文件并推送到GitHub

#### 3. 更新文章

1. 修改`issues/`目录下的Markdown文件
2. 保存并推送到GitHub
3. 系统会自动更新对应的Issue

#### 4. 删除文章

1. 从`issues/`目录删除Markdown文件
2. 推送更改到GitHub
3. 系统会自动关闭对应的Issue

### 工作原理

`issue-publisher.yml`工作流在检测到`issues/*.md`文件变更时触发，执行以下任务：

1. **变更检测**：识别新增、修改和删除的Markdown文件
2. **智能处理**：
   - 新增文件→创建新Issue
   - 修改文件→更新对应Issue
   - 删除文件→关闭对应Issue
3. **标签管理**：
   - 从文件提取标签(ISSUE_LABELS行)
   - 自动创建不存在的标签
   - 更新时保留原有标签
4. **状态恢复**：当重新添加已删除的文件时，自动重新打开对应Issue

### 特别说明

- 文件名会用作Issue标题，选择有意义的文件名以便识别
- 如果不指定标签，系统会应用默认的"文档"标签
- 支持中文文件名(自动处理转义序列)
- 删除文件不会真正删除Issue，而是将其关闭，方便日后恢复

### 完整工作流

1. 通过您喜欢的Markdown编辑器(如VS Code、Typora或[StackEdit](https://stackedit.cn/))编辑文章
2. 将文件保存到`issues/`目录
3. 推送到GitHub触发自动同步
4. Gmeek根据Issues自动构建博客页面

结合原版Gmeek的便捷性与增强版的本地编辑能力，您可以获得更加灵活高效的博客写作体验。
