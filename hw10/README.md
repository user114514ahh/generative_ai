# 作業10 HuggingFace復現上周彩貼生成器

```
prompt = "Cute 2D cartoon sticker, vibrant colors, thick bold black outline, sticker isolated on a solid black background (#000000), fun printable toy sticker style."

```

<img src="https://i.imgur.com/d1Cw80f.png" style="zoom:50%;" />

## 嘗試使用 Negative Prompt

```
Edmond Yip 參考來源https://blog.256pages.com/negative-prompts/
```

```
基本常用 negative prompts
worst quality, normal quality, low quality, low res, blurry, text, watermark, logo, banner, extra digits, cropped, jpeg artifacts, signature, username, error, sketch ,duplicate, ugly, monochrome, horror, geometry, mutation, disgusting
```

<img src="https://i.imgur.com/ewKNeI1.png" style="zoom:50%;" />

## 優化策略

1. Tokenization (斷詞/分詞/權杖化)
   1. NLP 自然語言模型基礎處裡步驟，將字串切割供進一步處理
2. Token 建立哈希表
3. One-Hot Encoding (獨熱編碼)

### 目的:

​	 將 Token 或類別特徵轉換成一個二元向量 (Binary Vector)，以解決數值編碼引入的人為順序問題。

### 方式：

​	基於詞彙表或類別列表的大小 N，創建一個長度為 N 的向量。

​	對於某個特定的 Token 或類別，其對應向量中，代表該項目的索引位置設為 1，其餘所有位置設為 0。

## 更換排程器pipe.scheduler

```
# 換成 UniPCMultistepScheduler
pipe.scheduler = UniPCMultistepScheduler.from_config(pipe.scheduler.config)
```

<img src="https://i.imgur.com/odl2kNJ.png" style="zoom:50%;" />

## 搜尋已經有的貼紙生成圖像模型

```
prithivMLmods/Ton618-Only-Stickers-Flux-LoRA
參考來源:Prithiv Sakthi
```

<img src="https://i.imgur.com/TJh5ez2.png" style="zoom:50%;" />

```
prompt = "cute rabbit sticker kawaii cat sticker, die-cut sticker, thick bold black outline, white border, flat design, simple shapes, vibrant pastel colors, isolated on black background"

```

​	<img src="https://i.imgur.com/z7XGcjD.png" style="zoom:50%;" />

#### 嘗試看看鮮豔的風格，看能不能升成類似插畫感

```
vibrant colors
```

<img src="https://i.imgur.com/G5s2DQB.png" style="zoom:50%;" />

這張圖看起來像是**一張放著貼紙、色紙和鉛筆的「照片」**，而不是單純的「貼紙圖案」本身

| 強調設計圖而非實物             | sticker design、sticker graphic、graphic art                 |
| ------------------------------ | ------------------------------------------------------------ |
| 隔離 純粹背景                  | isolated on a solid white background                         |
| 使用**負面提示詞**排除照片元素 | **排除照片感：** `photo`, `photograph`, `photography`, `realistic`, `real life`, `3D render`, `depth of field` (景深), `shadows` (陰影), `lighting` (光照效果) |
|                                | **排除場景和多餘物體：** `scene`, `objects`, `table`, `desk`, `background objects`, `pencil`, `crafts`, `paper cutouts`, `cluttered background` (雜亂背景) |

<img src="https://i.imgur.com/7gQwk56.png" style="zoom:50%;" />

<img src="https://i.imgur.com/MrjM67H.png" style="zoom:50%;" />