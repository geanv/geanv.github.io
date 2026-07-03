---
title: "Hello World"
description: "第一篇文章，记录一下这个博客的诞生，顺便展示 Markdown 的各种排版能力。"
date: 2026-06-28
tags: ["随笔"]
---

你好，世界！🎉

这是这个博客的第一篇文章。在经过一番选型之后，我决定用以下技术栈来搭建这个站点：

- **Astro** — 现代静态站点生成器，岛屿架构，默认零 JS
- **Tailwind CSS** — 实用优先的 CSS 框架
- **GitHub Pages** — 免费静态站点托管

## 为什么选择 Astro？

1. **性能优秀** — 默认输出纯 HTML，不发送 JavaScript，页面加载极快
2. **Markdown 原生支持** — 写文章就像写文档一样自然
3. **组件化** — 需要交互时可以引入任何 UI 框架
4. **SEO 友好** — 静态 HTML 对搜索引擎最友好

### 架构对比

Astro 的岛屿架构和传统 SPA 框架有本质区别：

| 特性 | Astro 岛屿 | Next.js SSR | 纯 SPA |
|------|-----------|-------------|--------|
| 默认 JS 体积 | 0 KB | 较大 | 很大 |
| 首屏加载 | 极快 | 快 | 慢 |
| 交互能力 | 按需加载 | 完整 | 完整 |
| SEO 表现 | 最佳 | 好 | 差 |

### 核心概念

Astro 有几个核心概念值得了解：

#### 零 JS 默认

Astro 默认不向客户端发送任何 JavaScript。这意味着你的页面就是纯 HTML + CSS，加载速度极快。只有标记为"岛屿"的组件才会被 hydrate。

#### 内容集合

Astro 的内容集合（Content Collections）提供了类型安全的 Markdown 管理方式：

```typescript
// src/content.config.ts
import { defineCollection, z } from 'astro:content';

const blog = defineCollection({
  loader: glob({ pattern: '**/*.md', base: './src/content/blog' }),
  schema: z.object({
    title: z.string(),
    description: z.string(),
    date: z.coerce.date(),
    tags: z.array(z.string()).default([]),
  }),
});
```

#### 岛屿架构

岛屿架构的核心思想是：**页面的大部分是静态的，只有交互区域需要 JavaScript**。这不仅减少了 JS 体积，还让页面更易于缓存。

> 静态优先，交互按需 —— 这是 Astro 的设计哲学。

## Markdown 排版演示

既然是第一篇文章，顺便把 Markdown 支持的排版元素都展示一下。

### 文本样式

- **粗体文本** 用于强调重要内容
- *斜体文本* 用于术语或语气强调
- ***粗斜体*** 两者结合
- `行内代码` 用于命令、变量名等
- ~~删除线~~ 表示过时或错误的内容

### 链接与引用

这是一个[示例链接](https://astro.build)，指向 Astro 官网。

> 好的工具不会限制你，而是让你专注于真正重要的事情。
>
> — 改编自某位工程师

### 代码块

一段 Python 示例：

```python
def fibonacci(n: int) -> list[int]:
    """生成斐波那契数列"""
    seq = [0, 1]
    for _ in range(2, n):
        seq.append(seq[-1] + seq[-2])
    return seq[:n]

print(fibonacci(10))
# [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

一段 Shell 命令：

```bash
# 创建新文章
cd src/content/blog
hugo new my-post.md

# 本地预览
npm run dev
```

### 有序与无序列表

技术选型时的考量优先级：

1. **性能** — 页面加载速度是用户体验的基石
   1. 首屏渲染时间 < 1s
   2. Lighthouse 评分 > 95
2. **开发体验** — 工具链应减少摩擦
   - 热更新要快
   - 类型安全要有
3. **部署成本** — 免费方案优先
4. **可维护性** — 技术债务不能越积越多

### 表格

一些常见的静态站点生成器对比：

| 工具 | 语言 | 模板引擎 | 构建速度 | JS 默认 |
|------|------|----------|---------|---------|
| Astro | JS/TS | Astro / JSX | 快 | 零 |
| Hugo | Go | Go Templates | 极快 | 零 |
| Next.js | JS/TS | React JSX | 中等 | 大 |
| 11ty | JS | 多种 | 快 | 零 |
| Jekyll | Ruby | Liquid | 中等 | 零 |

### 分隔线

以上是技术选型部分，以下是未来规划。

---

## 接下来的计划

- 持续更新技术文章
- 分享学习笔记和项目经验
- 记录有趣的发现和思考

### 短期目标

#### 七月

- 完成 Astro 主题定制
- 迁移历史文章
- 优化移动端体验

#### 八月

- 添加评论系统
- 集成站点搜索
- 优化 SEO 配置

欢迎常来看看！ 🚀
