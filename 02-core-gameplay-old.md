---
description: Soulbound Saga 採用完全上鏈的 Roguelike 架構，每個遊戲機制都透過智能合約實現真正的去中心化體驗。
---

# 2. 完全上鏈的 Roguelike 機制 (Fully On-Chain Roguelike)

#### **2.1 靈魂綁定資產 (Soulbound Assets)**

在 Soulbound Saga 中，每個資產都與玩家的靈魂契約永恆綁定，形成不可篡改的數位傳奇：

* **⚔️ 靈魂探索者 (Soul Delver NFT)**：您在靈魂紀元的化身。每位探索者都是獨特的 ERC-721 NFT，其「**數位力量 (Digital Power)**」由鏈上可驗證隨機數生成，代表著他們操控區塊鏈魔法的能力。
* **🔮 魂器 (Soul Relic NFT)**：連接探索者與區塊鏈的神秘裝置。其「**契約容量 (Contract Capacity)**」決定了可以同時綁定多少位探索者，是組建強大小隊的關鍵。
* **🏛️ 探索小隊 (Delver Squad NFT)**：革命性的組合式 NFT，將多個探索者和魂器組合成一個可交易的戰術單位。小隊的「**集體共識 (Collective Consensus)**」等於所有成員力量的總和。

> **🔗 技術亮點**：所有 NFT 都實現了 ERC-721 標準，並內建了鏈上元數據生成，確保每個資產的唯一性和可驗證性都完全存儲在 BNB Chain 上。

#### **2.2 程序地城探索 (Procedural Dungeon Delving)**

這是 Soulbound Saga 的核心 Roguelike 循環，每次探索都是獨一無二的鏈上冒險：

1. **啟動靈魂契約 (Initiate Soul Contract)**: 選擇探索小隊和目標程序地城，支付 **數位能量稅 (Digital Energy Tax, 以 BNB 計價)**。每個地城都有「**共識閾值 (Consensus Threshold)**」要求。

2. **區塊鏈隨機性 (Blockchain Randomness)**: 探索結果由 **Chainlink VRF** 或類似的鏈上可驗證隨機函數決定，確保每次冒險的公正性都可以被任何人驗證。

3. **$SOUL 挖掘 ($SOUL Mining)**: 成功的探索將獲得以 **USD 價值錨定的 $SOUL** 獎勵，以及 **靈魂經驗 (Soul Experience, SEXP)**。所有獎勵首先存入「**智能金庫 (Smart Vault)**」合約中。

4. **網路冷卻 (Network Cooldown)**: 每次探索後，小隊進入 **24 小時區塊時間冷卻**。這個機制確保了遊戲的可持續性和公平性。

> **⚡ Roguelike 特色**：每個程序地城都由智能合約即時生成，包含隨機的挑戰、獎勵和特殊事件，確保沒有兩次探索是完全相同的。

#### **2.3 玩家個人檔案 (Player Profile - SBT)**

玩家個人檔案是一個靈魂綁定代幣 (Soul-Bound Token, SBT)，它記錄了您在《Dungeon Delvers》世界中的所有成就與進程，是一個不可轉讓的榮譽象徵。

* **自動創建**: 當玩家首次完成地下城遠征並獲得經驗值時，系統會自動為其鑄造一個獨一無二的個人檔案 NFT。
* **經驗與等級**: 此 NFT 會記錄玩家累積的總經驗值（EXP）。經驗值的提升會帶來等級的成長（等級 = `sqrt(EXP / 100) + 1`）。
* **等級助益**: 玩家等級越高，在從金庫提領獎勵時，能享受越高的**稅率減免**。
* **動態鏈上藝術品**: 您的等級和經驗進度將透過靜態圖片展示。隨著您的等級提升，您個人檔案的視覺外觀也會變得更加炫酷。
