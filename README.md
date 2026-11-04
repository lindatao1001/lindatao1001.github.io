# 阳光满屋 · 房源展示页

青岛市南区一处一楼带院两室房源的**脱敏版**展示页，房东直租，供看房前预览户型、采光、家具家电与小区环境。

- 线上地址：<https://lindatao1001.github.io/>
- 页面形态：单个 HTML 文件，16 张图片以 base64 内嵌，**零外部依赖**，离线也能完整打开
- 脱敏口径：不含门牌号、手机号、微信号、二维码与具体租金，联系方式仅提示「通过平台私信联系房东本人」

## 文件说明

| 文件 | 作用 |
|---|---|
| `index0.html` | 脱敏版正本（单文件，含全部内嵌图片），改页面改这里 |
| `docs/index.html` | 线上发布入口，内容为 `index0.html` 的字节副本 |
| `docs/.nojekyll` | 发布标记：跳过 Jekyll 处理，静态文件按原样输出 |
| `.gitattributes` | 锁定换行，禁止 CRLF 转换，保证文件字节与线上一致 |
| `.gitignore` | 白名单规则：仅放行上述文件；本地完整版与原始照片一律不推送 |

> `index.html`（含租金与联系方式的完整版）只在本地保留，**不进本仓库**，由 `.gitignore` 排除。

## 本地预览

**方式一：直接打开**

双击 `index0.html`，用浏览器打开即可。图片已内嵌，无需联网。

**方式二：本地服务器（推荐，行为与线上一致）**

```bash
python -m http.server 8899 --bind 127.0.0.1
```

访问 <http://127.0.0.1:8899/index0.html>；验证根入口访问 <http://127.0.0.1:8899/docs/>。按 `Ctrl+C` 停止。

## 发布设置（GitHub Pages）

| 项目 | 取值 |
|---|---|
| 发布仓库 | `lindatao1001/lindatao1001.github.io`（本地 remote 名 `pages`） |
| 备份仓库 | `lindatao1001/my-first-website`（remote 名 `origin`，内容镜像） |
| 分支 | `main` |
| 发布目录 | `/docs` |
| 构建方式 | 分支部署（legacy），无需 Actions |
| 自定义域名 | 无，使用默认 `lindatao1001.github.io` |

> Pages 根路径只认 `index.html` 这个文件名，所以发布目录里必须放 `index.html`。
> 它只是 `index0.html` 的字节副本，不含完整版信息。

## 更新流程

```bash
# 1. 改 index0.html（脱敏版正本）
# 2. 同步发布副本
cp index0.html docs/index.html

# 3. 提交并推送
git add -A
git commit -m "更新房源页"
git push pages main
git push origin main
```

推送后 GitHub Pages 会自动构建，约 1 分钟内生效。
