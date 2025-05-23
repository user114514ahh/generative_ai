## 代碼改變的地方

### 新增state管理對話歷史

上一周的代碼

`messages = [{"role": "system", "content": systems[4]}]`

這樣的代碼只能用作初始化機器人的設定，為了讓機器人能保持連續對話，用gradio的state

`state = gr.State(initial_messages.copy())`

### 函數調整以支援連續對話

`mychatbot(prompt, madness_level)`

只回傳reply，不更新對話歷史，改為

`mychatbot(prompt, madness_level, messages)`

回傳內容為

`reply, messages`

### 新增函數submit_message

代替mychatbot，處理輸入、更新歷史、清空輸入框中的內容

清空輸入框中的內容:

`return chat_history, updated_messages, ""`

## 實際畫面預覽

可以看到，機器人能運作正常的和我進行**連續的對話**

| 我的輸入                          | 機器人接收訊息；拋出的問題           |
| --------------------------------- | ------------------------------------ |
| 我想要去裝個水                    | 你要著甚麼水；水要以甚麼方式來滋養你 |
| 水會讓我解渴我不知道 我到底要幹嘛 | 知道什麼樣的水，才能幫你解渴嗎       |
| 我要痛苦之河 我愛痛苦             | 你愛痛苦，這也是一種【共鳴】         |

![]()

<img src="螢幕擷取畫面 2025-04-14 190917.png" style="zoom: 33%;" />

<img src="螢幕擷取畫面 2025-04-14 190925.png" style="zoom:33%;" />

<img src="螢幕擷取畫面 2025-04-14 191144.png" style="zoom:33%;" />
