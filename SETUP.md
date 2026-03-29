# CBA 生物医药全球研发信息汇总 · GitHub Pages 部署说明

## 安全提示（必读）

- **永远不要在聊天、邮件里发送 GitHub 密码。** 若已泄露，请立即在 [GitHub → Settings → Password](https://github.com/settings/security) 修改密码并开启 **2FA**。
- 推送代码请使用 **SSH 密钥** 或 **Personal Access Token (PAT)**，不要使用账户密码。

## 一步步：把 `cba-github-pages` 加进你的 GitHub 账号

下面假设你只想把 **`Information/cba-github-pages/` 这一份网站** 放到一个新仓库里（最适合 GitHub Pages）。整个 `Information` 项目可以以后再单独建库备份。

### 第 1 步：在 GitHub 网页上新建空仓库

1. 浏览器打开 [https://github.com/new](https://github.com/new) 并登录。
2. **Repository name** 二选一：
   - **用户站点（网址最短）**：必须填 **`你的GitHub用户名.github.io`**（全小写，与 Profile 里 `@用户名` 一致）。
   - **项目站点（名字随便）**：例如 `cba-biopharma-site`，稍后访问地址会是 `https://用户名.github.io/cba-biopharma-site/`（并需在 `index.html` 里配置 `basePath`，见下文「方案 B」）。
3. 选 **Public**（GitHub 免费 Pages 对私有库有限制，公开最简单）。
4. **不要**勾选「Add a README」（保持空仓库，本机第一次推送最省事）。若已勾选了 README，见下方「若远程已有文件」。
5. 点 **Create repository**。记下页面上的仓库地址，例如：
   - HTTPS：`https://github.com/你的用户名/仓库名.git`
   - SSH：`git@github.com:你的用户名/仓库名.git`

### 第 2 步：在本机终端里推送（复制后改两处占位）

在 Mac 上打开「终端」，执行（把 `你的用户名` 和 `仓库名` 换成上一步的真实值）：

```bash
cd cba-github-pages

git init
git branch -M main
git add .
git commit -m "Initial: CBA global biopharma R&D summary site (Docsify)"
```

添加远程并推送（**任选一种**）：

**用 HTTPS（会提示登录；建议用 [Personal Access Token](https://github.com/settings/tokens) 代替密码）：**

```bash
git remote add origin https://github.com/你的用户名/仓库名.git
git push -u origin main
```

**用 SSH（需先在 GitHub 添加 [SSH key](https://github.com/settings/keys)）：**

```bash
git remote add origin git@github.com:你的用户名/仓库名.git
git push -u origin main
```

推送成功后，到 GitHub 网页刷新仓库，应能看到 `index.html`、`README.md`、`_sidebar.md` 等文件。

### 第 3 步：打开 GitHub Pages

1. 打开该仓库 **Settings → Pages**（左侧菜单）。
2. **Build and deployment** → Source：**Deploy from a branch**。
3. Branch 选 **main**，文件夹选 **/ (root)**，Save。
4. 等 1～3 分钟，同一页会出现站点地址；用户站点一般为 `https://你的用户名.github.io/`。

若是**项目站点**（仓库名不是 `用户名.github.io`），请按下面「方案 B」修改 `index.html` 里的 `basePath` 后再 push 一次。

### 若创建仓库时已经勾选了 README（远程先有文件）

在第一次 `git push` 前执行：

```bash
git pull origin main --rebase
```

若仍提示 unrelated histories，可改用：

```bash
git pull origin main --allow-unrelated-histories
```

解决冲突后再 `git push -u origin main`。

---

## GitHub 用户名与网址

- `xxx.github.io` 中的 `xxx` 是你的 **GitHub 用户名**（Profile 里的 `@名字`），**不是**邮箱地址。
- 手机访问示例：`https://你的用户名.github.io/`

## 方案 A：用户站点（推荐，网址最短）

1. 在 GitHub 新建仓库，仓库名必须为：**`你的用户名.github.io`**（全小写，与用户名一致）。
2. 把本目录 **`cba-github-pages/` 下的所有文件** 拷到该仓库根目录（或直接把本文件夹内容作为仓库根）。
3. 仓库 **Settings → Pages**：Source 选 **Deploy from branch**，Branch 选 **main**（或 **master**），文件夹 **/ (root)**，Save。
4. 等待 1～3 分钟，访问 `https://你的用户名.github.io/`。

## 方案 B：项目站点（仓库名任意，例如 `cba`）

1. 新建仓库名如 `cba`，将本站文件推到默认分支。
2. **Settings → Pages**：Branch 选默认分支，目录 **/ (root)**。
3. 打开 `index.html`，在 `window.$docsify = {` 内增加一行（注意末尾逗号）：

```js
basePath: '/cba/',
```

把 `cba` 换成你的**仓库名**。提交推送后访问：

`https://你的用户名.github.io/cba/`

## 本地预览（可选）

在项目根执行（需安装 [npx](https://docs.npmjs.com/cli/v8/commands/npx)）：

```bash
cd cba-github-pages
npx serve .
```

浏览器打开提示的本地地址（手机同一 WiFi 下可试 `http://电脑IP:端口`）。

## 与本仓库 `Information` 联动

生成周报后：

```bash
cp ../output/CBA03132026_跨平台发布成稿.md weekly/2026-03-20.md
```

编辑 `_sidebar.md` 加入该期链接，然后 `git add`、`commit`、`push`。

## GitHub Actions 自动部署（可选）

若站点源文件放在别的分支或目录，可用官方 **Pages workflow** 将构建结果推到 `gh-pages`。本站为纯静态 HTML + Markdown，一般 **直接推 main 即可**，不必 Actions。
