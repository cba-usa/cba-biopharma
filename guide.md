# 如何更新内容

## 1. 添加一篇周报

1. 在仓库里新建文件：`weekly/YYYY-MM-DD.md`（日期自定）。
2. 把 Markdown 正文粘贴进去并 **commit + push**。
3. 在 `_sidebar.md` 里加一行链接，例如：

```markdown
* [2026-03-20](weekly/2026-03-20.md)
```

（仓库在 **`用户名.github.io/仓库名/`** 子路径时，链接**不要**以 `/` 开头，否则跳到错误地址。）

把新链接放在列表**最上面**，读者最先看到最新一期。

## 2. 从本机生成再上传

若你在本地资料目录里用脚本生成了成稿，可将该 `.md` 复制到本仓库的 `weekly/` 下，按上一步推送即可。

## 3. 手机网址

启用 Pages 后，地址一般为：

- 用户站点：`https://你的GitHub用户名.github.io/`
- 项目站点：`https://你的GitHub用户名.github.io/仓库名/`

若是项目站点，需把 `index.html` 里 `basePath` 设为 `'/仓库名/'`（见 `SETUP.md`）。

## 4. 关键词、标签、比例条与地区展示

每篇周报可在文首或小结处插入 HTML，样式类名已写在 `index.html` 中。**可直接复制的长示例**见下文 [附录：HTML 片段示例](#cba-html-appendix)。

- **关键词** `cba-kw`、**标签** `cba-tag`（数据类可加 `cba-tag--stat`）
- **比例** `cba-pct-row` + `cba-pct-fill` 的 `width:__%`
- **国家/地区** `cba-geo-chip`：可写编辑摘要；若与 Plausible/GA4 后台一致，建议注明统计周期

<h2 id="cba-html-appendix">附录：HTML 片段示例（供周报粘贴）</h2>

将下面整段复制到任意 `.md` 正文中即可（可与 Markdown 混排）。首页不再放这些代码块，以免阅读干扰。

### 关键词 + 标签

```html
<div class="cba-doc-meta">
  <span class="cba-meta-label">关键词</span>
  <span class="cba-kw">ADC</span><span class="cba-kw">BD</span>
  <span class="cba-meta-label">标签</span>
  <span class="cba-tag">临床</span><span class="cba-tag cba-tag--stat">数据</span>
</div>
```

### 比例条

`cba-pct-fill` 的 `style="width:XX%"` 与右侧百分比数字保持一致。

```html
<div class="cba-pct-row" aria-label="美国 42%">
  <span class="cba-pct-name">美国</span>
  <div class="cba-pct-track"><span class="cba-pct-fill" style="width:42%"></span></div>
  <span class="cba-pct-val">42%</span>
</div>
```

### 读者国家 / 地区（手写摘要或引用后台统计）

```html
<p class="cba-meta-label" style="margin-bottom:0.25rem">本期访问来源（示例）</p>
<div class="cba-geo-row">
  <span class="cba-geo-chip"><strong>美国</strong> 48%</span>
  <span class="cba-geo-chip"><strong>中国</strong> 31%</span>
  <span class="cba-geo-chip"><strong>其他</strong> 21%</span>
</div>
```

## 5. 访问人数与国家地区（分析工具）

静态 Docsify 页面**无法**在不接入第三方服务的情况下自动显示「实时访客地图」。可选：

1. **Plausible**（无 Cookie、界面简单）  
   - 在 [Plausible](https://plausible.io) 添加你的网站域名（如 GitHub Pages 的 `cba-usa.github.io`）。  
   - 在本仓库 `index.html` 里找到 `window.CBA_SITE_CONFIG`，填写 `plausibleDomain: "你的域名"`。  
   - 推送后，在 Plausible 后台可查看访问量、国家/地区、来源页面等。

2. **Google Analytics 4**  
   - 创建媒体资源并取得 **衡量 ID**（`G-` 开头）。  
   - 在同一配置对象中填写 `ga4MeasurementId: "G-xxxxxxxxxx"`。  
   - 在 GA4 报表中查看「用户」→「用户属性」或「地理位置」等维度。

可同时只填一项。留空则**不加载**任何统计脚本。协会官网为 [cba-usa.org](https://cba-usa.org/)，本站为其志愿者维护的独立汇总页，与官网统计互不共用，除非你们另行统一配置。
