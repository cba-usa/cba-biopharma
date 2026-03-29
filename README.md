# CBA 生物医药全球研发信息汇总

面向手机与桌面浏览器；用于发布跨平台周报底稿与索引。

**主办组织（官网）**：[Chinese Biopharmaceutical Association, USA (CBA)](https://cba-usa.org/) — 美国华人生物医药协会，独立非营利专业组织；总部马里兰州，会员与活动信息以官网为准。联络可参考官网 [Contact](https://cba-usa.org/) 或邮件 **contact@cba-usa.org**。

## 本周

- 在左侧目录打开 **周报归档** 中最新一篇，或到 [指南](guide.md) 查看如何添加新文件。

## 说明

本站由 [Docsify](https://docsify.js.org/) 驱动，无需本地构建；将本仓库推送到 GitHub 并开启 **GitHub Pages** 后即可访问。

## 周报内可选：关键词、标签、比例、读者地区

在每篇 Markdown 里可使用 **HTML 片段**（与正文混排），站点已配好样式：

**关键词 + 标签**

```html
<div class="cba-doc-meta">
  <span class="cba-meta-label">关键词</span>
  <span class="cba-kw">ADC</span><span class="cba-kw">BD</span>
  <span class="cba-meta-label">标签</span>
  <span class="cba-tag">临床</span><span class="cba-tag cba-tag--stat">数据</span>
</div>
```

**比例条**（`cba-pct-fill` 的 `style="width:XX%"` 与右侧数字一致）

```html
<div class="cba-pct-row" aria-label="美国 42%">
  <span class="cba-pct-name">美国</span>
  <div class="cba-pct-track"><span class="cba-pct-fill" style="width:42%"></span></div>
  <span class="cba-pct-val">42%</span>
</div>
```

**读者国家/地区（手写摘要或引用后台统计）**

```html
<p class="cba-meta-label" style="margin-bottom:0.25rem">本期访问来源（示例）</p>
<div class="cba-geo-row">
  <span class="cba-geo-chip"><strong>美国</strong> 48%</span>
  <span class="cba-geo-chip"><strong>中国</strong> 31%</span>
  <span class="cba-geo-chip"><strong>其他</strong> 21%</span>
</div>
```

访问量与国家分布的**客观统计**需在 `index.html` 里配置 Plausible 或 GA4 后在对应后台查看；详见 [guide.md](guide.md)。
