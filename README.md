![](https://i.imgur.com/LPpcfoJ.png)

# 六角學院 2024 Vue 前端新手營第一週作業

這是六角學院 2024 Vue 前端新手營第一週的作業，作者為 Aaron。使用 Vue 3 和 Vite 來製作。

- [線上部署連結](https://hex2024-vue-homework1.worksbyaaron.com/)
- [作業文件連結](https://hackmd.io/O77_fHkGRnm8rPpMcOhh4g)

## 專案簡介

- **Vue 3 Composition API**：使用 Vue 3 的 Composition API 和 `<script setup>` 語法糖。
- **Vite 構建工具**：快速構建和開發環境。
- **響應式資料**：使用 `ref` 來管理響應式資料。
- **品項名稱編輯**：雙擊品項名稱即可進入編輯模式，可以儲存或取消編輯。
- **庫存管理**：可以增加和減少品項的庫存。

## 文件結構

```
├── src
│ ├── assets
│ │ └── AppStyle.css        App樣式文件
│ ├── data
│ │ └── items.js            品項資料
│ ├── App.vue               主要元件
│ └── main.js               入口文件
├── index.html              主 HTML 文件
├── package.json            專案配置文件
└── README.md               讀我檔案
```

## 快速開始

**專案設置（Project setup）**

將專案複製到本地端

```sh
$ git clone https://github.com/happyloa/Hex2024-Vue-Week1-Homework
```

套件安裝

```sh
$ cd Hex2024-Vue-Week1-Homework
$ npm install
```

**執行專案（Start the server）**

```sh
$ npm run dev
```

在瀏覽器上輸入

```
http://localhost:5173/
```

即可在本地端預覽專案

## 使用說明

### 編輯品項名稱

1.  雙擊品項名稱進入編輯模式。
2.  修改名稱後，點擊「儲存」按鈕保存更改，或點擊「取消」按鈕放棄更改。

### 管理庫存

1.  點擊「-」按鈕減少庫存。
2.  點擊「+」按鈕增加庫存。
