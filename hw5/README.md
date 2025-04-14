### 代碼與老師範例的不同

|                     | 老師範例                | 作業                                         |
| ------------------- | ----------------------- | -------------------------------------------- |
| system、description | 單一system、description | 使用陣列預設10個system、description          |
| gradio介面          | 使用iface               | 使用gr.block                                 |
| 介面元素            | -                       | 使用slider跟使用者交互調整癲狂程度、描述內容 |

### AI輔助的內容

介紹slider.change的基本用法和範例:

![](C:\Users\weian\桌面\螢幕擷取畫面 2025-04-05 193345.png)

提供思路完成十個設定變化和描述調整，透過建立並維護變數**madness_level**:

``

```
def update_description(madness_level):
  return descriptions[madness_level - 1]
```

### gradio介面截圖

![](C:\Users\weian\桌面\image.png)
