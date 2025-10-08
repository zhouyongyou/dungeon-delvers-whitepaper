# 15. 錢包相容性指南 (Wallet Compatibility Appendix)

> 適用版本：Soulbound Saga v1.5.0.0  
> 更新日期：2025 年 10 月 12 日  

## 15.1 支援的錢包與連線模式

- **MetaMask（桌面瀏覽器延伸套件）** – 建議版本 11.15 以上  
- **MetaMask / Trust Wallet / OKX App（行動裝置）** – 透過 WalletConnect v2 掃描 QR Code  
- **Brave / Rabby / Bitget / OKX 桌面版** – 走 `Injected` connector 後備模式  
- **硬體錢包** – 建議搭配 MetaMask 進行簽署（Ledger Live 仍在驗證中）  

> 提示：前端已預載 `metaMask`, `walletConnect`, `injected` 三類 connector，會依裝置自動選擇最佳路徑。

## 15.2 桌面環境建議流程

1. 安裝或更新 MetaMask（或支援 EIP-1193 的瀏覽器錢包）。  
2. 於 `https://www.dungeondelvers.xyz` 開啟遊戲，點擊右上角「連接錢包」。  
3. 在錢包清單中選擇「MetaMask」或「瀏覽器錢包」，瀏覽器將呼叫擴充功能並完成簽署。  
4. 如使用 OKX / Rabby 等非 MetaMask 錢包，請確認擴充功能允許對 BNB Chain 的授權。  
5. 若偵測不到任何 injected provider，請改用 WalletConnect 手機掃碼或檢查錢包是否被瀏覽器阻擋。  

## 15.3 行動裝置與 WalletConnect

1. 建議在行動裝置的預設瀏覽器（Safari / Chrome）開啟官方網站。  
2. 點選「連接錢包」後選擇 **WalletConnect**，畫面會顯示 QR Code 或直接跳出錢包列表。  
3. MetaMask / Trust Wallet / OKX App 會自動接管並詢問是否連線 BNB Chain。  
4. 若未顯示錢包彈窗，可在手機上手動打開該錢包 App，切換至「掃描」或「連接 DApp」頁籤貼上連線網址。  
5. 完成簽署後回到瀏覽器，頁面會自動更新連線狀態；若 30 秒內未完成，點擊「重新偵測」即可。  

## 15.4 PWA / 內建瀏覽器的特別注意事項

- **iOS PWA**：Apple 限制在 Home Screen PWA 中喚起第三方 App。系統會提示開啟 Safari，如長時間失敗請在彈窗選擇「於 Safari 開啟」。  
- **交易所 App 內嵌瀏覽器**：部分交易所禁止跨 App 呼叫錢包，建議改用手機預設瀏覽器或直接在錢包 App 內建的 DApp 瀏覽器輸入官方網址。  
- **安卓 WebView**：若看不到 QR Code，請關閉節電模式或切換至 Chrome；WalletConnect 會在低記憶體裝置中關閉動畫以提升穩定性。  
- **桌面 PWA**：Chrome 及 Edge PWA 皆支援 MetaMask 連線，但若擴充功能無法注入，可改用「瀏覽器錢包」選項或切換回原始分頁。  

## 15.5 常見問題與排解

| 問題情境 | 可能原因 | 解決方案 |
| --- | --- | --- |
| WalletConnect 顯示「Session expired」 | 連線逾時或錢包未回應 | 在遊戲頁面點擊「重新掃描」；若持續失敗請在錢包 App 的連線列表中刪除舊 Session 後再重試。 |
| 行動裝置顯示「無法開啟外部應用程式」 | 使用了交易所 App 內建瀏覽器 | 請改用 Safari / Chrome 或直接在錢包內建瀏覽器輸入官方網址。 |
| 錢包成功連線但列表顯示 0 NFT | 子圖仍在同步或 VRF 尚未完成 | 前端會顯示 202/Retry-After 提示，約 30–90 秒後自動更新；也可手動重整或使用「刷新資料」按鈕。 |
| MetaMask 在 PWA 中無法啟動 | PWA sandbox 限制 | 點擊提示中的「於原生瀏覽器開啟」，或直接在原始分頁使用。 |
| OKX/Bitget 桌面版無法連線 | 擴充功能尚未允許網站存取 | 於錢包擴充功能設定中加入 `https://www.dungeondelvers.xyz`，重新整理後選擇「瀏覽器錢包」。 |

## 15.6 建議的最佳實務

- 儘量使用最新版錢包 App / 擴充功能與桌面瀏覽器，保持與 WalletConnect v2 相容。  
- 完成連線後立即鎖定 BNB Chain，避免切換到不支援的網路。  
- 若需切換裝置，先在原裝置中按下「斷開連接」再重新掃描 QR Code，可避免 Session 殘留。  
- 測試與開發人員可透過 `window.__WALLET_DEBUG__`（僅在 DEV 模式啟用）檢視目前連線狀態與 connector。  

> 若仍遇到錢包相容性問題，請提供瀏覽器/錢包版本、裝置型號與錯誤截圖至官方 Discord #support 頻道，我們會在下一個迭代持續優化。 
