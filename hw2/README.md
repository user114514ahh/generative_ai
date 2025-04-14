![hw2_1](C:\Users\weian\桌面\hw2_1.png)

# 範例的運行嘗試

`N1 = 20

N2 = 20

N3 = 20`

![image-20250414204504339](C:\Users\weian\AppData\Roaming\Typora\typora-user-images\image-20250414204504339.png)

# 嘗試一 建構四層神經網路

`N1 = 128

N2 = 64

N3 = 32

N4 = 16`

![image-20250414204555941](C:\Users\weian\AppData\Roaming\Typora\typora-user-images\image-20250414204555941.png)

## 四層結果0.896 不如三層0.926

可能性:過度擬合
- 神經網路的層數和神經元數量增加導致模型的複雜度也跟著增加。如果訓練資料不足或模型過於複雜，可能會導致過度擬合，即模型在訓練資料上表現很好，但在驗證資料上表現變差。
- 增加 Dropout 層：在隱藏層之間加入 Dropout 層，隨機丟棄一部分神經元，防止過度擬合。

## 加入 Dropout

`from tensorflow.keras.layers import Dropout`

![image-20250414204804625](C:\Users\weian\AppData\Roaming\Typora\typora-user-images\image-20250414204804625.png)

表現大幅下降，可能是因為 Dropout 的使用增加了模型的複雜度，訓練時間的增加才可以讓模型良好的收斂

## 增加訓練時間

調整

`model.fit(x_train, y_train, batch_size=100, epochs=10)`

成

`model.fit(x_train, y_train, batch_size=100, epochs=100)`

![image-20250414205306914](C:\Users\weian\AppData\Roaming\Typora\typora-user-images\image-20250414205306914.png)

# 心得和總結

## **初始模型（三層神經網路）**

- **架構**：N1=20, N2=20, N3=20
- 結果：
  - Loss: 0.0117
  - 正確率: 92.7%
- 我先測試老師示範的三層神經網路（20-20-20），它的表現不錯，正確率達到 92.7%，比老師在課堂上的結果好一些，我想知道，如果增加模型的複雜度，是否能夠讓它更上一層樓？於是將模型擴展為四層（128-64-32-16）

## **增加模型複雜度（四層神經網路）**

- **架構**：N1=128, N2=64, N3=32, N4=16
- 結果：
  - Loss: 0.0153
  - 正確率: 89.7%
- 　結果出乎意料——正確率不升反降掉到了 89.7%。這讓我意識到，模型的複雜度並非越高越好，過多的層數和神經元可能會讓模型迷失在資料的海洋中，無法找到正確的方向。當然用專業一點的說法就是 over-fitting。

## **加入 Dropout 防止過度擬合**

- **架構**：四層神經網路 + Dropout（比率 0.5）
- 結果：
  - Loss: 0.0634
  - 正確率: 50.4%
- 　為了防止過度擬合，我加入 Dropout 層，並將比率設為 0.5。然而這一次的嘗試的正確率暴跌至 50.4%，我體會到，Dropout 雖然是一個強大的工具，但如果使用不當，反而會讓模型失去學習的能力。

## **調整訓練參數**

- 改進措施：
  - 增加訓練 Epochs 至 100
- 結果：
  - Loss: 0.0105
  - 正確率: 94.2%
- 　最後我增加了訓練的 Epochs 至 100。這一次，模型終於展現出了它的潛力，正確率提升到了 94.2%，Loss 值也顯著降低。這讓我明白，調參不僅需要勇氣，更需要細心與耐心。
- ![](C:\Users\weian\桌面\下載.png)
