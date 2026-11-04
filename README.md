# 阳光满屋 · 房源展示页

青岛市南区一处一楼带院两室房源的**脱敏版**展示页，房东直租，供看房前预览户型、采光、家具家电与小区环境。

- 线上地址：<https://lindatao1001.github.io/>
- 页面形态：单个 HTML 文件，16 张图片以 base64 内嵌，**零外部依赖**，离线也能完整打开
- 脱敏口径：不含门牌号、手机号、微信号、二维码与具体租金，联系方式仅提示「通过平台私信联系房东本人」

## 文件说明

| 文件 | 作用 |
|---|---|
| `index.html` | GitHub Pages 根入口，内容与 `index0.html` 逐字节相同 |
| `index0.html` | 脱敏版正本（单文件，含全部内嵌图片） |
| `.nojekyll` | 发布标记：跳过 Jekyll 处理，静态文件按原样输出 |
| `.gitignore` | 白名单规则：仅放行上述文件，原始照片与文案草稿一律不推送 |

> `index.html` 与 `index0.html` 是同一份内容的两个文件名。修改页面时请改 `index0.html`，再复制覆盖 `index.html`。

## 本地预览

**方式一：直接打开**

双击 `index0.html`，用浏览器打开即可。图片已内嵌，无需联网。

**方式二：本地服务器（推荐，行为与线上一致）**

在本目录执行：

```bash
python -m http.server 8899 --bind 127.0.0.1
```

然后访问 <http://127.0.0.1:8899/index0.html>。按 `Ctrl+C` 停止。

若需验证根路径入口是否正常，访问 <http://127.0.0.1:8899/>（读取 `index.html`）。

## 发布设置（GitHub Pages）

| 项目 | 取值 |
|---|---|
| 发布仓库 | `lindatao1001/lindatao1001.github.io`（本地 remote 名 `pages`） |
| 分支 | `main` |
| 发布目录 | `/`（根目录） |
| 构建方式 | 分支部署（legacy），无需 Actions |
| 自定义域名 | 无，使用默认 `lindatao1001.github.io` |

## 更新流程

```bash
# 1. 修改 index0.html 后同步根入口
cp index0.html index.html

# 2. 提交并推送（Pages 只认 pages 远端的 main 分支）
git add -A
git commit -m "更新房源页"
git push pages main
```

推送后 GitHub Pages 会自动构建，约 1 分钟内生效。
