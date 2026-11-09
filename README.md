# zslvmama 影片時序索引

兩個 YouTube 頻道全部影片的時序索引頁，同一條時間軸：

- [@zslvmama](https://www.youtube.com/@zslvmama)：媽媽在世時的影片，以及她走後我們想給她看的東西
- [@zslvtravel](https://www.youtube.com/@zslvtravel)：媽媽走後家人的旅遊，照片做成幾秒的影片一起放

🔗 **線上網址**：<https://zslvmama.github.io/youtube/>

## 內容

`index.html` 一個檔案，按標題前綴 date_token（拍攝日期時間）倒時序排列，最新在最上。
每列：縮圖 · 日期 · 標題 · 頻道標記（媽媽 / 旅遊）· V/S 標記 · 長度 → 點擊回 YouTube 看片。

頁首：

- 搜尋框即時過濾標題或日期，空格分隔多個關鍵字時全部命中才顯示（例：`金門 坑道`）。
- 「全部 / 媽媽 / 旅遊」切換只看一個頻道。
- 網址參數可直接指到過濾好的畫面：`?ch=mama|travel`、`?q=<關鍵字>`，例 <https://zslvmama.github.io/youtube/?ch=travel&q=金門>。頁面會把目前的過濾狀態寫回網址，複製即可分享。
- 「▶ 輪播」把目前列出的影片依拍攝時間由舊到新連續播放，全螢幕，播完再從頭。先用搜尋與頻道按鈕列出想看的那幾支（例如一趟旅遊），再按它。

## 說給媽媽聽

媽媽走後，兒子在農曆初一、十五把想讓她看的東西說給她聽，說的話一則一則寫在 [`forever`](https://github.com/zslvmama/forever) 的 `說/` 裡。這一頁可以把那些話和影片接在一起播：網址加 `?say=<說/ 檔名的一部分>`，多則用逗號分隔，例 <https://zslvmama.github.io/youtube/?say=金門>，按鈕會變成「▶ 說給媽媽聽」，先顯示那一則話，再播那一則的全部影片，接著下一則，全部播完再從頭。

一般的「▶ 輪播」不會顯示這些話。

## 更新方式

頁面從本機 build script 產生，兩個頻道的 TSV 與 `forever` 的 `說/` 一起讀（影片有增減、或 `說/` 有改動，都要重產）：

```bash
cd C:/zarsus/AI/workspace
python zslvmama/scripts/build_index_html.py
cd zslvmama/pages
git add index.html
git commit -m "Update: <date>"
git push
```

GitHub Pages 收到 push 後 ~1 分鐘自動重新部署。
