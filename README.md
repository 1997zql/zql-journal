# 郑强龙 · 随便记录点啥

一个极简、数据驱动的个人日记站点：页面结构在 `index.html`，内容全部写在 `posts.json`。

## 本地预览

因为页面会通过 `fetch` 读取 `posts.json`，请用本地静态服务器打开，不要直接双击 HTML。

```bash
# Python
python3 -m http.server 8080

# 或 Node
npx --yes serve -p 8080
```

浏览器访问：http://127.0.0.1:8080

## 写一篇新日记

编辑根目录的 `posts.json`，在 `posts` 数组**最前面**加一条：

```json
{
  "date": "2026.11.24",
  "weekday": "周二",
  "content": "今天把日记站完善了一下，标签筛选和搜索终于能用了。",
  "tags": ["想法", "站点"]
}
```

字段说明：

| 字段 | 说明 |
| --- | --- |
| `date` | 显示日期，推荐 `YYYY.MM.DD` |
| `weekday` | 星期几，可省略 |
| `content` | 正文 |
| `tags` | 标签数组，用于筛选 |

站点文案（标题、介绍、金句、关于、页脚链接）写在同一文件的 `site` 字段里。

## 页面能力

- 标签筛选：顶栏芯片或日记下方标签均可点击
- 关键词搜索：匹配正文 / 标签 / 日期，并高亮命中
- 状态可分享：筛选条件会写入地址栏 `#tag=量化&q=交易`
- 离线兜底：`posts.json` 加载失败时，仍显示页面内置备份内容

## 部署

这是纯静态站点，适合 GitHub Pages / Cloudflare Pages / 任意静态托管。

GitHub Pages 示例：仓库 Settings → Pages → Source 选 `main` 分支根目录。
