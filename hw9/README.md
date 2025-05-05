# Diffusion Model實作與提示詞工程

## 目標：生成商業素材風格貼圖

- #### 線條簡約，具有設計感

- #### 方便後續使用

- #### 貼紙視覺效果（白底黑色粗線條）

- #### 可以穩定生成上述風格的提示詞

## 範例：

<img src="https://i.imgur.com/urRBk8e.png" alt="https://i.imgur.com/urRBk8e.png" style="zoom: 50%;" />

<img src="https://i.imgur.com/7PN20Jb.png" style="zoom: 50%;" />

## 初次嘗試

<img src="https://i.imgur.com/67ikC2G.png" alt="https://i.imgur.com/67ikC2G.png" style="zoom:50%;" />

效果良好，具有手繪感，設計感，背景也是純色。適合photoshop去背（有商業素材感）

#### 改進的方向

<img src="https://i.imgur.com/GReaIbW.png" style="zoom:50%;" />

非常糟糕的生成，畫面不完全。列印的話不像是貼紙；作為多媒體素材使用也不能透過軟體簡單的修正(內容缺失)

| minimalist flat design       | 確保扁平設計   |
| ---------------------------- | -------------- |
| graphic design element       | 確保簡約       |
| prominent bold black outline | 貼紙特效       |
| centered composition         | 確保畫面不缺失 |



## 第二次嘗試

<img src="https://i.imgur.com/vzhdrCt.png" style="zoom:50%;" />

提示的內容可能含有誤導ai以為要求的方向是icon

#### 改進的方向

| minimalist flat design                  | 移除                 |
| --------------------------------------- | -------------------- |
| graphic design element                  | 移除                 |
| Cute 2D cartoon sticker, vibrant colors | 確保基本符合貼紙要求 |
| fun printable toy sticker style         | 確保基本符合貼紙要求 |

## 第三次嘗試

<img src="https://i.imgur.com/XKpzkzy.png" style="zoom:50%;" />

雖然大致方向正確(貼紙風格設計、適合後續使用)，但提到鮮豔設計又是灰階另一邊的極端，看似更符合街頭塗鴉還有網路meme

## 最終嘗試

經過幾次產生的內容偏移原本訂定的方向，把幾個會偏差的提示詞移除，留下可以保證要求的提示詞(版面設置的要求基本不會出錯)，修正一些細節後可以得到：

<img src="https://i.imgur.com/OGU1LGm.png" style="zoom:50%;" />

<img src="https://i.imgur.com/mRdCs75.png" style="zoom:50%;" />

<img src="https://i.imgur.com/9QQ4gDy.png" style="zoom:50%;" />

### 整體可以透過多次修正來排除錯誤的元素，並留下最基本的提示詞來達成要求，第四點的通用性也基本可以實現，不管是用來教育製作簡報，還是提供靈感都有一定的功能，重點是要把想要的Ｏｂｊｅｃｔ用英文表達，可以生成更加準確的圖像。