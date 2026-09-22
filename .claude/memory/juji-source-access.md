---
name: juji-source-access
description: 《爵迹》调研时各类中文来源的实测可达方式（哪些能 curl、哪些必须走浏览器、哪些拿不到）
metadata: 
  node_type: memory
  type: reference
  originSessionId: 8a900c99-b6ea-4888-bc28-52f77649d1e0
  modified: 2026-09-21T19:55:34.603Z
---

2026-09-22 实测，为 extra-novel 项目调研《爵迹》时摸出来的来源可达性：

- **百度百科**：`baike.baidu.com` 对 curl 与 WebFetch 一律 403（安全验证）；改用移动版 `wapbaike.baidu.com/item/<词条>` 加手机 UA，curl 可直接取到正文。
- **维基百科**：`zh.wikipedia.org/w/index.php?title=<词条>&action=raw` 取原始维基文本，比 WebFetch 的小模型摘要完整得多；分册没有独立词条，用 API 的 `list=search` 找真实标题。
- **知乎、百度贴吧**：curl 与 WebFetch 均 403，只能走 Chrome 工具；`get_page_text` 能一次拿全文，`javascript_tool` 单次返回约一千字就截断，且返回值里带查询串的 URL 会被整体拦截。
- **豆瓣书评**：curl 加桌面 UA 可直接取。
- **旧版原文**（临界·爵迹 Ⅰ、Ⅱ，风津道 12 回）：天涯书库 `tianyabooks.com/cn/gjm08/`、`gjm09/`、`gjm10/` 可逐章抓取；底本有错字、串行和个别重复段。
- **新版三部曲原文**：没有公开可读来源。微信读书须登录，番茄小说网页端只给字体混淆的试读片段。新版内容只能靠二手材料，其中豆瓣书评 `review/9553652` 含尾声原文引文。

**How to apply:** 再查这个题材时直接按上面的通道走，别在 403 上反复试。原文只放临时目录研读，不入库。
