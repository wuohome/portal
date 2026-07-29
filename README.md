# 窩的家企業入口

全公司同仁的第一頁：<https://wuohome.github.io/portal/>

## 這個 repo 只有入口本身

系統頁面（39 支）住在另一個 repo `wuohome/ragic`，網址是 `https://wuohome.github.io/ragic/*.html`。

**那些網址不能搬。** 定金收據、退款確認之類的連結是 Ragic 自動寄給房東房客的，網址寫死在 Ragic 的信件範本裡，搬了外部使用者就打不開。

因此本 repo 用絕對路徑引用另一邊，**不留副本**：

| 引用的東西 | 路徑 | 為什麼不複製一份過來 |
|---|---|---|
| `js/shared.js` | `/ragic/js/shared.js` | 裡面有人名別名表與管理層名單，兩份會走鐘 |
| 卡片連結 | `index.html` 的 `SYS_BASE = '/ragic/'` | 加系統只要改 `GROUPS`，不用改路徑 |
| Logo | `/ragic/assets/wuohome-logo.png` | 同上 |

⚠️ `wuohome/ragic` 這個 repo 若改名，本頁會整個壞掉。

`https://wuohome.github.io/ragic/` 舊入口留了一支自動跳轉頁指到這裡，同仁手上的舊連結不會失效（規則：發出去的連結永不更換）。

## 檔案

| 檔案 | 做什麼 |
|---|---|
| `index.html` | 殼：身分、部門分眾卡片、三圓環佔位、搜尋、掛載點 |
| `js/portal-board.js` | 公布欄（管理層發布／置頂／刪除） |
| `js/portal-moods.js` | 心情留言板（全體同仁） |
| `js/portal-api.js` | 兩支模組共用的 Worker 呼叫封裝與錯誤訊息對照 |

資料一律走 `wuohome-ragic-proxy` Worker，前端沒有任何金鑰。公告與留言存在 Supabase `portal_posts` / `portal_moods`。

## 規格

- 產品：`窩的家/系統部/規格書/窩的家企業入口_規格書`
- 介面凍結點：`窩的家/系統部/規格書/窩的家企業入口_前端契約_公布欄與留言板`
- 視覺：`窩的家/系統部/規格書/移植12系統_視覺基準` § 01
