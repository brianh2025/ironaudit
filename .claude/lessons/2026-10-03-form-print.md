雲端環境用 Playwright 測 index.html：需 ignoreHTTPSErrors，並等待 CDN 載入完成再操作。

- 雲端 session 的對外 HTTPS 走代理，Chromium 不認代理 CA，CDN（jsdelivr）載入失敗會出現 `htm is not defined`。`newPage({ignoreHTTPSErrors: true})` 即可。
- CDN 載入時間不固定，固定 sleep 2.5 秒偶爾不夠；改用 `waitForSelector('text=＋ 新增專案')`。
- 「＋ 新增」同時出現在頁首（新增專案）與紀錄表（新增紀錄），選擇器要限定在 `main .card`。
- 表單列印頁的 `.psheets` 在螢幕上隱藏，裡面也有 `tbody tr`；選清單列要用 `.noprint tbody tr`。
- 驗證分頁：`emulateMedia({media: 'print'})` 後 `page.pdf()`，數 PDF 頁數即可確認每張表單一頁。
