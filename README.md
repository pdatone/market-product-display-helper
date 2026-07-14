# 🧱 市集擺攤陳列模擬器

輸入桌子尺寸、建立自己的陳列道具，在 2D 俯視圖上拖曳擺位，右側即時同步 3D 預覽——出攤前先在電腦上把桌面配置演練一遍。

## 功能特色

- **自訂桌子尺寸**：輸入寬／深／高（cm），畫面依實際比例呈現
- **物件庫**：建立自己的商品與道具（名稱、寬高深、顏色），支援三種形狀：
  - 方塊：一般商品、盒子、立牌
  - 階梯展示架：可自訂 2–8 層，3D 會呈現實際階梯造型
  - 洞洞板：直立板身，厚度固定 2cm
- **2D 編輯**：拖曳移動、旋轉 90°（R）、複製（D）、刪除（Del），可選 1cm 或 5cm 格點吸附
- **防呆警示**：物件重疊或超出桌面時，2D 與 3D 同步變紅提醒
- **3D 預覽**：拖曳旋轉視角、滾輪縮放，模擬客人站在攤位前看到的樣子
- **自動存檔**：配置自動存在瀏覽器中，關掉重開不會消失

## 開始使用

### 方法一：直接在線上使用（推薦給朋友）

若這個 repo 已開啟 GitHub Pages，直接打開：

```
https://pdatone.github.io/market-product-display-helper/
```

（repo 擁有者開啟方式：GitHub repo → Settings → Pages → Source 選 `Deploy from a branch`，Branch 選 `main`、資料夾選 `/ (root)`，儲存後等一兩分鐘即可。）

### 方法二：下載到自己電腦執行

因為頁面使用了 ES Modules，不能直接雙擊 HTML 檔開啟，需要一個本機靜態伺服器：

```bash
git clone https://github.com/pdatone/market-product-display-helper.git
cd market-product-display-helper
python3 -m http.server 8123
```

然後用瀏覽器打開 `http://localhost:8123`。

- macOS 內建 Python 3，直接可用
- Windows 使用者可安裝 [Python](https://www.python.org/downloads/)，或改用 VS Code 的 Live Server 擴充功能
- 若出現 `Address already in use`，把 `8123` 換成其他數字（例如 `8124`）再試

## 操作說明

| 操作 | 方式 |
|------|------|
| 設定桌子 | 左側輸入寬／深／高，按「套用桌子尺寸」 |
| 建立道具 | 左側表單填名稱、寬高深、形狀、顏色，按「＋ 新增到物件庫」 |
| 擺上桌面 | 點物件旁的「加入」，會自動找空位放置 |
| 移動 | 在 2D 俯視圖直接拖曳 |
| 旋轉／複製／刪除 | 先點選物件，再按工具列按鈕或快捷鍵 `R`／`D`／`Del` |
| 3D 視角 | 在右側預覽區拖曳旋轉、滾輪縮放 |

## 常見問題

**我的配置存在哪裡？**
存在瀏覽器的 localStorage，只在同一台裝置、同一個瀏覽器有效。清除瀏覽器網站資料會一併清掉。

**可以把配置傳給朋友嗎？**
目前還不行，匯出／匯入功能在規劃中。

## 技術說明

純前端專案，零框架、零建置流程：原生 JavaScript + SVG（2D）+ [Three.js](https://threejs.org)（3D，已內附於 `vendor/`，離線可用）。
