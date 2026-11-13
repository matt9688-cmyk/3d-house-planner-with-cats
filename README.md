# 🏡 1F 房屋格局與家具自由擺放設計家 (1F Home Layout & Furniture Designer)

> **Version**: `v3.1` — 40-Ping Layout · Realistic 3D Cats (Skeleton/Coat Customizer & 2.5D A\* Pathfinding) · Voxel-Brick Conversion · Tatami/Loft Mezzanine · Rolling/Sliding Doors  
> **Live App Entry**: [`index.html`](./index.html) (Zero-install single-file HTML, ready for GitHub Pages)  
> **Tech Stack**: Three.js (r128) + Tailwind CSS + WebGL 3D + 2D Blueprint Overlay + `InstancedMesh` Voxel Engine + 2.5D A\* Navigation  
> **Language**: [English Overview](#english-overview) ｜ [繁體中文操作手冊](#一v30-重點更新與特色)

---

## English Overview

### Key Features (`v3.1`)
- **40-Ping (`132.3 m²`) Ground & Flexible Aspect Presets**: Switch between Square (`11.5m × 11.5m`), Wide (`13.25m × 10.0m`), Townhouse (`16.5m × 8.0m`), or enter custom `W × D` dimensions.
- **Single-End Anchored Wall Stretching**: Drag the Cyan (`A`) or Emerald (`B`) endpoint handle to resize walls without shifting the opposite anchor; supports endpoint snapping and <kbd>Shift</kbd> free-angle adjustment.
- **53+ Furniture Items with Multi-Size Presets & Dual-Color Materials**: Customize `W / D / H`, dual colors, and procedural textures (Marble, Wood, Fabric, Matte, Metal, Tatami).
- **Japanese Washitsu, Mezzanine Loft & Rolling/Sliding Doors**: Build elevated tatami rooms, wooden mezzanines with single-sided/storage stairs, electric rolling shutters, and shoji/barn track doors with adjustable open ratios.
- **🧱 One-Click Pixel / Voxel Brick Conversion**: Transform the entire house into LEGO-style bricks with top studs via `THREE.InstancedMesh` (`0.18m` / `0.25m` / `0.35m` resolution) and export voxelized `.obj` models.
- **🐱 Realistic Articulated 3D Cats & Customizer**:
  - Smooth spline-lofted torso, 3-segment articulated limbs, blinking slit-pupil eyes (with heterochromia), procedural coat patterns (`bicolor`, `tabby`, `calico`, `solid`, `siamese`), and 8 skeleton/proportion sliders (including **70% lightning-kink tail** & **100% straight tail**).
  - **2.5D A\* Cross-Room & Stair/Mezzanine AI**: Cats navigate through opened doors, avoid solid furniture, hop onto tatami/sofas, climb wooden stairs up to the mezzanine loft (`上樓`), and chase the **🔴 Laser Pointer** across rooms.
- **Save / Load & Export**: Auto-save to `localStorage`, export/import `.json` (`v3.1`, backward-compatible with `v2.0`/`v3.0`), 2D blueprint `.png`, and 3D `.obj`.

### Quick Controls
- **2D / 3D / FPV Views**: Switch anytime from the top bar (<kbd>W</kbd><kbd>A</kbd><kbd>S</kbd><kbd>D</kbd> + <kbd>Q</kbd>/<kbd>E</kbd> in FPV).
- **Edit**: <kbd>R</kbd> Rotate 45° · <kbd>D</kbd> Duplicate · <kbd>Delete</kbd> Remove · <kbd>Ctrl</kbd>+<kbd>Z</kbd>/<kbd>Y</kbd> Undo/Redo · Arrow keys nudge (`0.25m` / <kbd>Shift</kbd> `0.05m`).

---

## 一、v3.0 重點更新與特色

### 1. 📐 預定 40 坪基地地坪（132.3 m²）與多比例切換
- 預設地坪大小設定為 **40.0 坪**（`11.5m × 11.5m = 132.25 m²`）。
- 可於右側「**基地地坪設定**」一鍵切換不同 40 坪長寬比例：
  - **方正 40 坪**（`11.5m × 11.5m`）
  - **寬面 40 坪**（`13.25m × 10.0m`）
  - **長透天 40 坪**（`16.5m × 8.0m`）
- 亦可直接輸入任意面寬 `W` 與深度 `D`（公尺），即時換算坪數與 $m^2$。

### 2. 🧱 牆壁「單邊錨定伸縮」（解決雙邊拉長跑位問題）
- 點選牆壁後，兩端會顯示 **A 端（青色）** 與 **B 端（翠綠色）** 控制球：
  - **拖曳 B 端**：A 端完全固定不動，僅向 B 端延伸或縮短。
  - **拖曳 A 端**：B 端完全固定不動，僅向 A 端延伸或縮短。
  - 拖曳端點接近其他牆端點時會自動**磁吸對齊**接角；若按住 <kbd>Shift</kbd> 拖曳端點，則可同時自由調整牆面角度與長度。
- 右側面板「**調整長度時的固定端**」亦可切換 `固定 A 端`、`中心對稱`、`固定 B 端`，點擊 `-0.5m / +0.5m / +1.0m` 或滑桿微調時也不會讓牆壁跑位。

### 3. 📏 家具多重尺寸規格 & 自由長寬高調校
- 選取任一家具（如 **沙發、電冰箱、床組、餐桌、茶几、衣櫃、塌塌米、電捲門、樓中樓**），右側面板會自動顯示專屬「**快速尺寸規格選擇**」按鈕：
  - **電冰箱**：單門小冰箱 (0.55m) / 雙門中冰箱 (0.72m) / 對開大冰箱 (0.92m) / 日製多門 (0.85m) / 旗艦加大 (1.05m)。
  - **沙發**：單人座 / 雙人座 / 三人座 / 四人加大 / 多款 L 型轉角沙發。
  - **塌塌米**：1 帖 / 2 帖 / 4.5 帖 / 6 帖 / 8 帖。
- 亦可直接修改 **面寬 W / 深度 D / 高度 H** 數值，系統會即時重建精細 3D 幾何模型。

### 4. 🎨 全家具雙色調色盤與表面質感紋理
- 所有家具（含 **大理石雙層茶几**、中島、沙發、冰箱、門窗、和室等）均支援：
  - **主體色**與**輔色／框架／腳座／塌塌米緣**獨立調色。
  - **表面質感切換**：自動預設、🏛️ **大理石紋**（支援卡拉拉白、黑金花、雲霧灰、翡翠墨綠、暖米洞石等任意大理石底色）、🪵 **實木木紋**、🧶 **布藝織紋**、✨ **霧面烤漆**、⚙️ **金屬拉絲**。

### 5. 🍵 新增「日式和室」與「塌塌米」空間系統
- 左側新增「**🍵 日式和室**」分類：
  - 日式塌塌米地墊（支援多種帖數尺寸與布邊緣調色）
  - 架高木質和室地台（含木踏階與側邊收納抽屜）
  - 和室實木矮桌 (茶几)、日式坐墊組、日式和室鋪床組、茶具置物矮櫃、日式木格柵屏風
- 房間區域（Room Zones）支援「**🍵 日式編織塌塌米**」與「**🌲 日式檜木木地板**」，並可設定**地坪架高高度（如 +35cm 架高和室）**。

### 6. 🚪 新增「電捲門」與「軌道拉門」
- 左側「**🚪 捲門/拉門**」分類新增：
  - **電動鐵捲門**：含頂部捲門箱、側導軌與波浪門片，支援 1.5m～5.2m 單/雙車庫尺寸，右側面板可即時調整**開啟比例（0% 關閉～100% 全開）**。
  - **單片吊軌拉門（穀倉門）**：外露上吊軌與滾輪五金，可調整開啟滑動距離與木色。
  - **雙片軌道玻璃拉門**：鋁框雙軌玻璃連動拉門，支援大小尺寸與開啟比例調整。
  - **日式障子軌道雙拉門**：和室專用木格柵紙拉門。

### 7. 🏗️ 新增「木製樓中樓」與「單面木梯」（支援家具擺上二層夾層）
- 左側新增「**🏗️ 樓中樓/梯**」分類：
  - **木製樓中樓夾層**：包含實木樓板、底部托樑、落地木柱，可自由勾選前/後/左/右四側欄杆、設定「**前欄杆留梯口（1.1m）**」及「**樓板半透明**」（方便透視編輯樓下家具）。
  - **單面直行實木樓梯**、**單面階梯收納木梯（階梯櫃）**、**單面斜靠閣樓木梯**：可切換左側/右側/雙側/無扶手，並自由搭配樓中樓高度。
- 任一家具均支援調整 **Y 離地高度 (m)**，選中家具後點擊「**⬆️ 放上樓中樓/地台**」即可一鍵放到夾層或架高和室上方！

---

## 二、快捷鍵與視角操作指南

| 操作行為 | 滑鼠操作 | 鍵盤快捷鍵 | 功能說明 |
| :--- | :--- | :---: | :--- |
| **單邊伸縮牆長** | 拖曳牆端 A / B 球體 | 按住 <kbd>Shift</kbd> | 固定另一端點單邊伸縮；按住 Shift 可同時改角度 |
| **連續畫牆/結束** | 點擊畫布兩點 | <kbd>ESC</kbd> | 自動磁吸牆端點，按 ESC 退出畫牆 |
| **微調移動物件** | 左鍵拖曳 | <kbd>↑</kbd><kbd>↓</kbd><kbd>←</kbd><kbd>→</kbd> | 每次移動 0.25m（搭配 <kbd>Shift</kbd> 每次 0.05m） |
| **復原 / 重做** | 點擊頂部還原鈕 | <kbd>Ctrl</kbd>+<kbd>Z</kbd> / <kbd>Y</kbd> | 支援最多 40 步歷史紀錄復原與重做 |
| **旋轉 / 複製 / 刪除** | 右側屬性面板 | <kbd>R</kbd> / <kbd>D</kbd> / <kbd>Delete</kbd> | 旋轉 45° / 原地複製 / 刪除選取物件 |
| **2D 平圖縮放平移** | 滾輪縮放 / 右鍵拖曳 | - | 檢視尺寸標註、房間坪數與門窗/樓梯符號 |
| **FPV 第一人稱走訪** | 左鍵拖曳環顧 | <kbd>W</kbd><kbd>A</kbd><kbd>S</kbd><kbd>D</kbd> + <kbd>Q</kbd>/<kbd>E</kbd> | 屋內走動並可用 Q/E 升降視高上樓中樓參觀 |

---

## 三、自動存檔與成果匯出
1. **瀏覽器自動暫存**：編輯結果會自動暫存於本機 `localStorage`，重新整理不遺失；亦可於右側底部點擊「重置為 40坪 預設範本」清除暫存。
2. 💾 **儲存 / 載入專案 (.json)**：向下相容舊版 `v2.0` / `v3.0` 格局檔並支援 `v3.1` 完整屬性（含自訂貓咪陣列 `catConfigs`）。
3. 📸 **匯出 2D 平面格局圖 (.png)**：自動合成房間名稱、坪數、牆長尺寸與基地圖框資訊。
4. 🧊 **匯出 3D 幾何模型 (.obj)**：完整匯出牆體、樓中樓樑柱欄杆、木梯踏階與全屋家具細部幾何，可直接匯入 Blender 或 Unity。


---

## v3.1 寫實 3D 貓咪 × 像素積木風格整合說明

### 1. 寫實 3D 貓咪建模與骨架外觀自訂（點選「🐱 貓外觀」或直接點擊 3D 貓咪）
- **平滑寫實結構**：捨棄分段球體，改用連續樣條放樣軀幹（Lofted Spine Torso）、三段式關節貓腿（肩/大腿、膝/前臂、肉墊貓掌）、可眨眼上下眼瞼＋垂直細縫瞳孔（支援**雙眼異色瞳**）、三角粉鼻、內耳廓、鬍鬚與 6 節平滑漸細尾巴。
- **預設雙貓保留特徵**：
  - **花花**：橘白背毛色、70% 閃電折角尾。
  - **咪咪**：灰虎斑條紋、100% 直長尾。
- **可調外觀與骨骼參數**：
  - 體型/骨骼：`整體大小`、`身長`、`圓潤度`、`腿長`、`頭型大小`、`耳朵大小`、`尾巴長度`、`閃電尾折角 (0°~45°)`。
  - 花紋與毛色：支援 `雙色賓士/橘白背 (bicolor)`、`虎斑 (tabby)`、`三花 (calico)`、`純色 (solid)`、`暹羅重點色 (siamese)`，並可自由調色（主毛色、條紋/副色、肚/白襪色、左眼色、右眼色、鼻/耳廓色），亦可一鍵套用 6 種快速品種預設或 `+ 新增` 多隻貓咪（自動寫入 `.json` 存檔與瀏覽器自動暫存）。

### 2. 貓咪自由活動與互動
- **自由 AI 與避障**：貓咪在屋內自由走動時會自動閃避牆體，並偶爾前往「寵物雙碗餵食器 (`cat_feeder`)」進食，或前往「雲朵貓窩 / 日式塌塌米 (`cat_bed_cloud` / `tatami_mat`)」休息。
- **互動姿態**：可針對單隻貓咪切換 `自由AI`、`散步`、`上樓`（一鍵走樓梯登上木製樓中樓夾層）、`坐下`、`趴睡`、`吃飯`，面板下方即時顯示標高 `Y`、路點數與 `A*` 雙層網格狀態。
- **🔴 逗貓棒（雷射筆）**：點擊頂部「`🔴 逗貓棒`」後，在地面移動滑鼠即可投射紅色雷射光點，吸引屋內所有貓咪快速追逐！

### 3. 🧱 像素 / 積木風格房屋轉換
- 點擊頂部「`🧱 積木風格`」即可將定稿後的 40坪 房屋（地板、房間區、牆壁、樓中樓、樓梯、電捲門/拉門與全屋家具）即時轉換為帶凸點（Studs）的 **3D 積木風格**，採用 `THREE.InstancedMesh` 批次渲染保持流暢操作。
- 右側面板可切換積木顆粒解析度：**精細 `0.18m`** / **標準 `0.25m`** / **大積木 `0.35m`**，並即時顯示積木總顆數。
- **積木模式下的貓咪互動與匯出**：在積木房屋內貓咪依然可自由走動與追逐逗貓棒；點擊「`🧊 匯 3D`」可直接匯出積木版 `.obj` 幾何模型；再次點擊「`🧱 積木風格`」即可無損切回寫實編輯模式繼續修改格局。
- **2.5D A* 跨房尋路與樓梯／樓中樓行走**：貓咪會透過 A* 尋路網格自動繞過隔間牆與實心家具，從開啟的軌道拉門／房門穿梭不同房間（如客廳 → 和室 → 餐廚），並能沿著單面實木梯或階梯收納木梯走上木製樓中樓夾層巡邏與休息（爬梯時身體會隨坡度自然微傾）。
