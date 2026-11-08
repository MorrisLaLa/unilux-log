# unilux-log

一六工程日誌的手機入口（GitHub Pages：`https://morrislala.github.io/unilux-log/`）。程式本體在 Apps Script（原始碼：MorrisLaLa/unilux-v6）。

| 檔案 | 用途 |
|---|---|
| `index.html` | 手機主畫面圖示的入口：從圖示打開（或網址帶 `?go`）直接進系統；用瀏覽器打開時顯示「加到主畫面」說明 |
| `labels.html` | 物料／批次 QR 標籤列印頁（A4 24 格 70×37mm），由系統「📦 物料進出 → 📊 庫存統計 → 🏷️ 列印標籤」打開 |
| `qrcode.js` | QR Code Generator for JavaScript v1.4.4（Kazuhiko Arase，MIT），原檔未修改，`labels.html` 用 |
| `manifest.webmanifest`、`icon-*.png` | 加到主畫面用的名稱與圖示 |

## 物料 QR 標籤

- 物料標籤：`https://morrislala.github.io/unilux-log/?m=物料代號`
- 批次標籤：`https://morrislala.github.io/unilux-log/?m=物料代號&b=批次碼`

手機相機掃描後，`index.html` 把格式正確的 `m`、`b` 轉給系統網址（`APP`），系統直接打開「物料進出」並選好物料（批次）。
QR 裡放的是這個入口頁的網址、不是 Apps Script 網址：以後 Apps Script 網址換了只要改 `index.html` 的 `APP`，已經貼出去的標籤不用重印。

`labels.html` 的標籤資料放在網址 `#` 後面（base64url 的 JSON），不會送到任何伺服器。
列印時縮放選「實際大小／100%」、邊界選「無」；頁面上可設「從第幾格開始」（接著用印過一半的標籤紙）和「位置微調」（記在該台電腦）。
