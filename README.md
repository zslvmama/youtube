# zslvmama 影片索引

[YouTube 頻道 @zslvmama](https://www.youtube.com/@zslvmama) 全部影片的時序索引頁。

🔗 **線上網址**：<https://zslvmama.github.io/youtube/>

## 內容

`index.html` — 1670 支影片，按標題前綴 date_token（拍攝日期時間）倒時序排列。
每列：縮圖 · 日期 · 標題 · V/S 標記 · 長度 → 點擊回 YouTube 看片。
頂端有搜尋框可即時過濾標題或日期。

## 更新方式

頁面從本機 build script 產生：

```bash
python zslvmama/scripts/build_index_html.py
cd zslvmama/pages
git add index.html
git commit -m "Update: <date>"
git push
```

GitHub Pages 收到 push 後 ~1 分鐘自動重新部署。
