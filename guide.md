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

若你在 `Information` 项目里用脚本生成了成稿，可将该 `.md` 复制到本仓库的 `weekly/` 下，按上一步推送即可。

## 3. 手机网址

启用 Pages 后，地址一般为：

- 用户站点：`https://你的GitHub用户名.github.io/`
- 项目站点：`https://你的GitHub用户名.github.io/仓库名/`

若是项目站点，需把 `index.html` 里 `basePath` 设为 `'/仓库名/'`（见 `SETUP.md`）。

## 4. 关键词、标签、比例条与地区展示

每篇周报可在文首或小结处插入 HTML，样式类名已写在 `index.html` 中，示例见 [README.md](README.md) 的「周报内可选」一节。

- **关键词** `cba-kw`、**标签** `cba-tag`（数据类可加 `cba-tag--stat`）
- **比例** `cba-pct-row` + `cba-pct-fill` 的 `width:__%`
- **国家/地区** `cba-geo-chip`：可写编辑摘要；若与 Plausible/GA4 后台一致，建议注明统计周期

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
