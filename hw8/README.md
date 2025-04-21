# 範例一 Aisuite

### 函式 reply 常用 API 參數

| temperature | 控制回覆的隨機性和創造力（值越高越隨機）               |
| ----------- | ------------------------------------------------------ |
| max_tokens  | 限制回覆的最大長度                                     |
| top_p       | 另一種控制隨機性的方法（值越高越可能包含較不常見的詞） |
| stop        | 設定模型生成到特定字串時停止                           |

### 調整參數的結果

![](C:\Users\weian\桌面\w7\3.png)

![](C:\Users\weian\桌面\w7\4.png)

![](C:\Users\weian\桌面\w7\5.png)

![](C:\Users\weian\桌面\w7\6.png)

除了預先用 system 規劃生成內容，調整參數也能大幅度改變生成的內容

# 範例二 產生器CoT

### `W4` V.S. `W7`

| 特性 / 概念    | W4                                      | W7                                             |
| -------------- | --------------------------------------- | ---------------------------------------------- |
| AI 角色        | 單一 Chatbot 角色                       | Planner (規劃者) / Writer (寫作者) 兩階段角色  |
| System Prompts | 10 個提示給單一角色 (控制聊天風格/任務) | 10 組 (共 20 個) 提示，Planner/Writer 各 10 個 |
| 核心邏輯流程   | 單一步驟:使用者輸入 -> 生成回復         | Planner to `Schedule`; Writer to `FinalPost`   |
| -              | -                                       | `call_groq_api`                                |

### call_groq_api

無論程式是順利執行完 `try` 區塊並進入 `if` 分支，還是 `try` 區塊執行失敗直接跳到 `except` 區塊，這個函式在**所有預期的執行路徑結束時，都必須有一個 `return` 語句**

![](C:\Users\weian\桌面\w7\7.png)

### 傳遞數據和ai互動流程設計

`generation_prompt` 的構建 (`f"計畫如下：{schedule}根據它寫一段..."`) 是一個典型的 **Prompt Engineering** 技巧，這也說明了跟原本的代碼不同的地方，兩個模型的協作產生的多階段生成，用`planner`跟`writer`;`schdule`跟`finalPost`區分

![](C:\Users\weian\桌面\w7\8.png)

### Gradio介面

![](C:\Users\weian\桌面\w7\1.png)

![](C:\Users\weian\桌面\w7\2.png)