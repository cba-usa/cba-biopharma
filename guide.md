# 如何更新内容

## 1. 添加一篇周报

1. 在仓库里新建文件：`weekly/YYYY-MM-DD.md`（日期自定）。
2. 把 Markdown 正文粘贴进去并 **commit + push**。
3. 在 `_sidebar.md` 里加一行链接，例如：

```markdown
* [2026-03-20](/weekly/2026-03-20.md)
```

把新链接放在列表**最上面**，读者最先看到最新一期。

## 2. 从本机生成再上传

若你在 `Information` 项目里用脚本生成了成稿，可将该 `.md` 复制到本仓库的 `weekly/` 下，按上一步推送即可。

## 3. 手机网址

启用 Pages 后，地址一般为：

- 用户站点：`https://你的GitHub用户名.github.io/`
- 项目站点：`https://你的GitHub用户名.github.io/仓库名/`

若是项目站点，需把 `index.html` 里 `basePath` 设为 `'/仓库名/'`（见 `SETUP.md`）。
