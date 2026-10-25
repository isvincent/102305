# 法國秋季風暴｜2026 學生抗議到全國暴動（9:16 教學影片網頁）

以 **單一 HTML ＋ 內嵌 SVG** 製作的直式（1080×1920）自動播放教學簡報，手機開啟就像看一支短影片：
每頁有動態視覺化、轉場效果、女聲語音旁白，以及與旁白同步逐句出現的字幕。

> 內容整理至 **2026 年 10 月 25 日**。事件仍在發展，課堂使用前請再確認最新消息。

## 內容大綱（12 頁，約 4 分鐘）

| 頁 | 主題 | 視覺化 |
|---|---|---|
| 01 | 封面：法國秋季風暴 | 法國輪廓＋巴黎擴散波紋 |
| 02 | 起點：9/21 克雷泰伊聖修伯里高中 | 地圖定位、周邊學校擴散點 |
| 03 | 學生四大訴求 | 數據卡片、溫度計動畫 |
| 04 | 兩週內擴散全國 | 時間軸長條成長、數字跳動 |
| 05 | 三股不滿匯流 | 三條路徑描繪匯聚至 10.17 |
| 06 | 10/17 失控的一夜 | 人數計數器、城市火點地圖 |
| 07 | 用數字看衝擊 | 橫條圖＋累計數據 |
| 08 | 政府兩手策略 | 隨旁白傾斜的天平 |
| 09 | 兩大爭議 | 正反並陳＋62% 民調環圈 |
| 10 | 10/24 第二波遊行 | 兩日人數對比長條 |
| 11 | 外溢到歐洲 | 擴散網絡示意圖 |
| 12 | 課堂討論三問題 | 問題卡片＋資料來源 |

## 功能

- **自動播放**：按下開始後逐句朗讀、逐句顯示字幕，頁面自動切換；畫面元素依旁白進度同步出現。
- **語音旁白**：瀏覽器內建語音合成（Web Speech API），語速 1.15（中等稍快），自動挑選繁體中文女聲（如 iOS「美佳」、Windows「HsiaoChen」、Google 國語）。
- **字幕**：每段不超過兩行，可用「CC」按鈕開關。
- **轉場**：圓形展開、橫向擦除、上升、縮放、推入、百葉等 6 種。
- **控制**：播放／暫停、上一頁、下一頁、字幕、語音開關；手機可左右滑動換頁；鍵盤 空白鍵／←／→／C／M。
- **RWD**：1080×1920 畫布等比縮放至任何螢幕，不變形、不裁切。
- **PWA**：可「加入主畫面」，以全螢幕獨立 App 開啟，離線也能播放（字型首次連網後快取）。
- **播放時螢幕不休眠**（支援 Wake Lock 的瀏覽器）。

## 檔案結構

```
france-unrest-2026/
├── index.html              # 首頁（全部 HTML / CSS / SVG / JS）
├── manifest.webmanifest    # PWA 設定
├── sw.js                   # Service Worker 離線快取
├── .nojekyll               # 讓 GitHub Pages 直接提供檔案
├── README.md
└── icons/
    ├── icon.svg
    ├── icon-192.png
    ├── icon-512.png
    └── icon-maskable-512.png
```

## 部署到 GitHub Pages

1. 在 GitHub 建立新的公開儲存庫，例如 `france-unrest-2026`。
2. 把本資料夾所有檔案（含 `icons/` 與 `.nojekyll`）上傳到儲存庫根目錄。
3. 進入 **Settings → Pages**，Source 選 **Deploy from a branch**，Branch 選 `main`、資料夾 `/ (root)`，按 Save。
4. 約一分鐘後即可從 `https://<你的帳號>.github.io/france-unrest-2026/` 開啟。

指令列版本：

```bash
git init
git add .
git commit -m "法國秋季風暴 教學影片網頁"
git branch -M main
git remote add origin https://github.com/<你的帳號>/france-unrest-2026.git
git push -u origin main
```

> PWA 與 Service Worker 需要 HTTPS，GitHub Pages 已預設提供。直接雙擊本機 HTML 也能播放，只是不會啟用離線功能。

## 使用提醒

- **第一次播放需點一下「開始」**：手機瀏覽器規定語音必須由使用者點擊觸發。
- 手機請關閉**靜音模式**（iPhone 側邊開關），否則語音合成可能無聲。
- 語音音色取決於裝置內建語音；若裝置沒有中文語音，會自動改為「無聲＋字幕計時」模式繼續播放。
- 若要錄成影片檔：手機用內建螢幕錄影，或電腦以瀏覽器視窗調成直式後錄製。

## 修改旁白或內容

逐字稿集中在 `index.html` 底部的 `SLIDES` 陣列：

```js
{ c:[ "第一句字幕與朗讀內容",
      ["畫面顯示的文字", "實際朗讀的文字"],   // 英文或需調整發音時使用
      "第三句" ] }
```

- 每個字串＝一次出現的字幕＋一段語音，建議每句 ≤ 24 字。
- 畫面元素加上 `data-b="n"`，就會在第 n 句（從 0 起算）時出現。
- 語速改 `const RATE = 1.15;`。
- 修改後若已安裝 PWA，請把 `sw.js` 的 `VERSION` 改成新值（例如 `fr26-v2`），使用者才會拿到新版本。

## 資料來源

- CNN：〈Clashes in France after day of mostly peaceful protests〉（2026/10/24）、Macron 全國談話報導（2026/10/17–19）
- Al Jazeera：〈Hundreds of thousands protest in France amid heightened police security〉（2026/10/24）
- CNBC：〈More than 500,000 took to the streets as France protests erupted into violence〉（2026/10/19）
- BBC、Reuters、Le Monde、franceinfo 等報導（經 Wikipedia〈2026 French student protests〉〈2026 French fuel protests〉條目彙整）
- 美國駐法大使館安全警示（2026/10/22）
- Bella 儂儂〈法國爆發嚴重暴動！事件起因與發展懶人包〉（2026/10/22）

人數以法國內政部等官方統計為主；工會、主辦單位的估計通常較高，頁面中已並列說明。
各方立場（政府、人權團體、政黨）以並陳方式呈現，供課堂討論，不代表特定立場。

## 授權

教學用途自由使用與改作；新聞內容版權屬原媒體所有。
