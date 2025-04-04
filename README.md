# HimDocs-Builder

[繁體中文](README.md) | [English](README_EN.md)

# HimDocs-Builder

## 介紹

HimDocs-Builder是一個簡單而強大的文檔站點生成器，使用 HTML、CSS 和 JavaScript 構建。它支援動態側邊欄、目錄（TOC）、主題切換（淺色/深色模式）、進度條以及 Markdown 內容渲染。使用者可以通過修改 `pages.json` 配置文件來定義站點結構和內容，並支援自訂頁尾版權資訊。

### 特點
- **動態側邊欄**：根據 `pages.json` 自動生成巢狀菜單。
- **路由支援**：點擊菜單項時更新 URL 哈希（例如 `#page1`），支援瀏覽器前進/後退。
- **主題切換**：支援淺色和深色模式，切換時有平滑過渡效果。
- **Markdown 渲染**：使用 `marked.js` 將 `.md` 文件渲染為 HTML。
- **進度條**：顯示內容區的滾動進度。
- **頁尾動畫**：內容滑到底部後繼續向下滾動時，頁尾彈出。
- **自訂性**：支援自訂標題、頁尾版權文字和菜單圖標。

你可以在此預覽最新版本的HimDocs-Builder:
https://himservice-docs.himserver.com/
## 安裝

### 條件
- Python 3.9 或更高版本。

### 步驟
1. **複製專案文件**
   - 將以下文件放入你的專案目錄：
     - `index.html`：主頁面結構。
     - `style.css`：樣式文件。
     - `script.js`：核心邏輯。
     - `pages.json`：站點配置、頁面配置文件。
     - `content/`：存放 Markdown 文件的目錄（例如 `page1.md`）。
     - `server.py`：啟動、端口配置。
     - `assets/`：你可以在此放置你的logo只需命名成logo的.png檔案
2. **設置內容**
   - 在 `content/` 目錄中創建 Markdown 文件，例如：
     ```
     # 歡迎頁面
     這是我的第一個文檔頁面。
     ```
     文件名應與 `pages.json` 中的 `path` 對應（例如 `page1.md`）。
3. **配置啟動端口**
   - 前往server.py更改
	 ```bash
     # 定義伺服器端口
	  PORT = 8000
     ```
     將 PORT = `8000` 改成你的端口
4. **啟動伺服器**
   - 在專案目錄下運行：
     ```bash
     py server.py
     ```
   - 控制台將顯示 `服務器運行於 http://localhost:8000`
   - 在瀏覽器中訪問 `http://localhost:8000`。

## 使用說明

### 瀏覽站點
- **首頁**：打開 `http://localhost:8000`，預設載入 `pages.json` 中第一個有 `path` 的頁面。
- **切換頁面**：點擊側邊欄菜單項，URL 會更新（例如 `#page2`），內容區顯示對應的 Markdown 文件。
- **主題切換**：點擊右上角的 `🌙`（深色模式）或 `☀️`（淺色模式）按鈕。
- **搜索**：在搜尋欄輸入關鍵字，過濾側邊欄菜單項。
- **頁尾**：滾動到內容底部後繼續向下滾動，頁尾會彈出。

### 示例 Markdown 內容
在 `content/page1.md` 中：
```
# 第一頁
這是我的文檔內容。

## 子標題
- 項目 1
- 項目 2
```

渲染後：
- 標題和列表正常顯示。
- 連結顯示為可點擊的超連結。

## 自訂選項

### 自定義 `pages.json`
配置文件位於 `pages.json`，結構如下：
```json
{
    "title": "我的文檔站點",
    "footerCopyright": "© 2025 我的文檔站點",
    "sidebar": [
        {
            "name": "專案 A",
            "path": "page1",
            "icon": "🏠",
            "children": [
                {
                    "name": "模組 A-1",
                    "path": "subpage1-1"
                }
            ]
        },
        {
            "name": "專案 B",
            "path": "page2",
            "icon": "🚀"
        }
    ],
    "settings": {
        "theme": "light",
        "language": "zh",
        "showIcons": true
    }
}
```
- **`title`**：站點標題，顯示在頁面標題和頁首。
- **`footerCopyright`**：頁尾版權文字（僅限修改此部分，後綴固定為 `| Powered by HimService`）。
- **`sidebar`**：定義側邊欄菜單，支持巢狀結構。
  - `name`：菜單項名稱。
  - `path`：對應的 Markdown 文件名（不含 `.md`）。
  - `icon`：可選的圖標（例如 emoji）。
  - `children`：子菜單項。
- **`settings`**：
  - `theme`：預設主題（`light` 或 `dark`）。
  - `language`：語言設置（目前僅支援 `zh`）。
  - `showIcons`：是否顯示圖標（`true` 或 `false`）。

### 自訂樣式
編輯 `style.css`：
- **主題顏色**：修改 `body.dark` 的 `background` 和 `color`。
- **連結顏色**：調整 `.content a` 和 `body.dark .content a` 的 `color`。

## 已知問題

## 開發與貢獻

### 報告問題

如果發現 bug 或有功能建議，請在 GitHub 創建 Issue，提供詳細描述和重現步驟。

## 許可證

請閱讀 `LICENSE` 文件。
