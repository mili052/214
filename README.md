# 新游测试周报（含 GitHub Pages 看板）

本目录用于沉淀**2月9日至14日**期间的新游测试周报，并通过 **GitHub Pages** 生成一个可视化看板网页（Kanban）。

## 目录结构

- `reports/`：周报文件（Markdown）
- `docs/`：GitHub Pages 静态站点（直接渲染看板）

## 如何在 GitHub 上生成看板网页（GitHub Pages）

### 方式 A（推荐）：GitHub Actions 一键部署

1. 在 GitHub 新建一个仓库（例如：`game-test-weekly-report`），并把本目录上传到仓库根目录（包含 `docs/` 与 `.github/workflows/pages.yml`）。
2. 打开仓库 **Settings → Pages**：
   - **Build and deployment** 选择 **GitHub Actions**
3. 之后每次 push 更新 `docs/**`，都会自动部署到 Pages。

### 方式 B：从分支直接部署（不走 Actions）

1. 在 GitHub 新建一个仓库（例如：`game-test-weekly-report`）。
2. 将本目录所有文件上传到该仓库根目录。
3. 打开仓库 **Settings → Pages**：
   - **Build and deployment** 选择 **Deploy from a branch**
   - **Branch** 选择 `main`（或你的默认分支）
   - **Folder** 选择 `/docs`
4. 保存后等待 1-2 分钟，Pages 会给出一个站点地址。
5. 打开站点即可看到看板页面（`docs/index.html`）。

## 如何更新内容

- 周报：编辑 `reports/2026-02-09_to_2026-02-14.md`
- 看板数据：编辑 `docs/kanban.json`
  - 页面会自动读取该 JSON 并渲染卡片
- 看板周报页：编辑 `docs/report.md`

## 如何把“图片卡片”贴到看板上

可以，推荐做法是把图片文件放进仓库，再在 `docs/kanban.json` 里引用相对路径（这样 GitHub Pages 才能稳定加载）。

1. 把图片复制/粘贴到：`docs/assets/`（例如 `docs/assets/doupo.png`）
2. 在 `docs/kanban.json` 对应条目增加字段（`rankChanges/tests/watchPoints` 都支持）：

```json
{
  "name": "斗破苍穹",
  "image": "./assets/doupo.png"
}
```

说明：
- `image` 也可以填外链图片 URL，但更建议放进仓库，避免外链失效。
- GitHub Pages 是静态站点：**直接在网页里 Ctrl+V 粘贴图片不会自动保存到仓库**；需要把图片文件提交到仓库里。

