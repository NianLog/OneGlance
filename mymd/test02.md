# 数据结构与算法笔记

<span class="important-note">本笔记专为计算机专业学生和算法爱好者设计，涵盖数据结构的核心知识点和常用算法实现。</span>

这是一份关于**数据结构与算法**的学习笔记。

## 目录

1. 数组
2. 链表
3. 栈与队列
4. 树与图
5. 排序算法

### 时间复杂度对比

| 算法 | 平均时间复杂度 | 空间复杂度 | 稳定性 |
|------|---------------|-----------|--------|
| 冒泡排序 | O(n²) | O(1) | 稳定 |
| 快速排序 | O(n log n) | O(log n) | 不稳定 |
| 归并排序 | O(n log n) | O(n) | 稳定 |

<span class="tip-box">面试高频考点：快速排序的平均时间复杂度为O(n log n)，但最坏情况为O(n²)，需要注意优化。</span>

```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)
```

<span class="warning-box">注意：递归实现的快速排序可能会导致栈溢出，对于大规模数据建议使用迭代版本或改用归并排序。</span>

> 算法是解决问题的步骤，数据结构是存储数据的方式。二者相辅相成，缺一不可。