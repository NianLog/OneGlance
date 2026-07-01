# 文档编写规范

## 快速开始

新增文档时，请参考 `mymd/template.md` 模板文件。

## 必填元素

### 1. 文档开头重要提示

```markdown
<span class="important-note">简要说明本文档的主题和内容，让读者快速了解文档的核心要点。</span>
```

### 2. 章节结构

- 使用 `##` 作为大章节标题
- 使用 `###` 作为小节标题
- 使用 `####` 作为更细分的小节（可选）

### 3. 代码块

```markdown
```python
def example():
    print("Hello, World!")
```
```

## 可选元素（建议添加）

### 提示框样式

| 样式 | 用法 | 示例 |
|------|------|------|
| `tip-box` | 学习技巧、补充说明 | `<span class="tip-box">提示内容</span>` |
| `warning-box` | 注意事项、常见错误 | `<span class="warning-box">警告内容</span>` |

### 示例

```markdown
<span class="tip-box">面试高频考点：快速排序的平均时间复杂度为O(n log n)。</span>

<span class="warning-box">注意：递归可能导致栈溢出，对于大规模数据建议使用迭代版本。</span>
```

## 标题层级示例

```markdown
# 文档标题（仅用于SEO，通常显示在页面顶部）

## 第一章：主题名称

### 1.1 具体概念

#### 细分概念（可选）
```

## 表格示例

```markdown
| 列1 | 列2 | 列3 |
|------|------|------|
| 内容 | 内容 | 内容 |
```

## 注意事项

1. 所有文档放在 `mymd/` 目录下
2. 文件名使用 `testXX.md` 格式（如 `test09.md`）
3. 在 `config.json` 中添加文档配置
4. 密码统一使用 `123456`
5. 代码块必须标注语言类型（python/java/javascript/c/sql等）
