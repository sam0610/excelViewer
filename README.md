# Excel 編輯器 (excelViewer)

純網頁嘅 Excel / CSV 開啟同編輯工具。唔使安裝伺服器,唔使登入任何帳戶,資料只喺你部電腦嘅瀏覽器入面處理,唔會上傳。

## 功能

- 開啟 `.xlsx` `.xlsm` `.xls` `.csv`(拖放或按「開啟檔案」)
- 顯示並保留 `.xlsx` 嘅格式:顏色、字型、框線、對齊、欄寬列高、合併儲存格、凍結窗格、數字格式
- 直接改儲存格、公式列、公式即時重算(`+ - * /`、`SUM` `AVERAGE` `MIN` `MAX` `COUNT` `ROUND` `ABS` `IF`)
- 拖曳或 Shift+方向鍵選取多格,複製、剪下、貼上、清除
- 插入或刪除列和欄,復原(Ctrl+Z),多工作表
- 儲存為 `.xlsx`(Ctrl+S),或匯出目前工作表為 CSV

## 使用

網址(開啟 GitHub Pages 後):<https://sam0610.github.io/excelViewer/>

或者喺本機行:

```sh
python3 -m http.server 8000
# 然後用瀏覽器開 http://localhost:8000
```

## 儲存方式

| 瀏覽器 | 儲存 |
| --- | --- |
| Chrome / Edge | 彈出「另存新檔」視窗,可揀位置;揀返原檔會由系統確認是否取代 |
| Safari / Firefox | 下載成新檔,放喺瀏覽器下載位置 |

程式唔會靜默覆蓋原檔。

## 設為 Excel 預設開啟程式(Mac)

1. 用 Chrome 或 Edge 打開網址,選單入面選「安裝 Excel 編輯器」(Chrome:網址列右邊嘅安裝圖示;Edge:選單 → 應用程式 → 將此網站安裝為應用程式)。
2. 喺 Finder 揀一個 `.xlsx` 檔,按 Command+I(取得資訊),喺「打開方式」揀「Excel 編輯器」,再按「全部更改⋯」。
3. 之後雙擊 Excel 檔就會用呢個程式開。

已安裝嘅程式離線都可以用。有新版本時,連網開啟會自動更新。

## 已知限制

- 儲存時唔會保留:圖表、圖片、條件式格式、資料驗證(下拉選單)、巨集、樞紐分析表。
- `.xls`、`.ods` 同 CSV 只讀到資料,冇格式。
- 公式只支援上面列出嘅函數。其他函數會顯示檔案內原有嘅結果,用 Excel 開啟會重新計算。
- 開啟有密碼保護嘅檔案會失敗。

## 檔案

- `index.html`:整個程式(單一頁面)
- `lib/`:第三方元件 [SheetJS](https://sheetjs.com/) 0.18.5(Apache-2.0)、[ExcelJS](https://github.com/exceljs/exceljs) 4.4.0(MIT)
- `manifest.webmanifest`、`sw.js`、`icon*`:安裝成應用程式、註冊開啟 Excel 檔同離線使用
