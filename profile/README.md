# PTT 飛鴿傳書

## 用於 PTT 新文章提醒的服務 (支援 Line、Telegram) 
此服務實際上也是我對於微服物架構的一個練習，  
因此在某些程式中可能會看到一些過度設計，或是不必要的模式出現  
因為是練習嘛 XD

### Feature :  
1. 整合 Line Login 第三方登入
2. 整合 Telegram Login Widget 第三方登入
3. 使用者可對 PTT 任一看板訂閱 主題 / 作者
4. Line User 利用 Line Notify 進行通知
5. Telegram User 利用 Bot 進行通知

--- 


### Architecture :
![Architecture](https://raw.githubusercontent.com/PTT-Post-Notify/.github/main/profile/Architecture.drawio.png)

綠色部分已開發、設定完成  
黃色部分開發中

Key Point :  
- 整個服務拆成數個 Service 並放在 GCP 
- 基本上均使用 GCP Cloud Run 來節省費用
- 使用 Cloud Function 來 Trigger Article Monitor (每小時執行一次)
- 主服務 (LineUserService、TelegramUserService) 使用 Event Sourcing 來建立可追蹤及重現的使用者操作紀錄
- 各 Service 之間的通訊使用 GCP Pub/Sub 來推播

---

如果真有人願意加入專案  
請留言或 Mail 給我，我會把你加入 Member   
chris03152008@gmail.com
