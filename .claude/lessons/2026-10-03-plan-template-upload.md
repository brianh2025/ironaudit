雲端測 index.html 時 jsdelivr CDN 常 ERR_TOO_MANY_RETRIES；先 curl 下載函式庫，再用 Playwright `ctx.route` 本地供應即可穩定。

- 路由 `https://cdn.jsdelivr.net/npm/**`，把 URL 的 `/` 換成 `_` 當檔名，`fulfill({path})`；含 pdfjs worker 也可用。
- 專案已存在時畫面沒有「＋ 新增專案」歡迎頁；導覽是分組的，表單列印要先點「填報」群組。
- 無法取得使用者的監造計畫樣本時，以 `page.pdf()` 產生含文字層的測試 PDF、python zipfile 組最小 docx、`XLSX.write` 產生 xlsx，三種格式都能測。
- 自動辨識監造計畫的表單（以標題字尾與列文字推測）效果差，改為使用者上傳空白表單範本、點選儲存格對應欄位：結構（儲存格文字、合併、欄寬）存成 JSON 而非 HTML，列印時依範本重畫，避免 innerHTML。需要真實格式才能做的功能，先要使用者提供範本，不要憑猜測做自動解析。
- 測試腳本別用 sed 全域取代檔名，會連同 `writeFileSync` 一起改而覆寫測試檔。
