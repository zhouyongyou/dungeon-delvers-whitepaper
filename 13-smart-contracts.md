# 13. 智能合約地址 (Smart Contract Addresses)

> **🎯 V1.5.0.0 正式合約地址** - 全面升級，正式版本上線

## 13.1 核心提醒

✅ **最新正式版本**：以下為 V1.5.0.0 正式環境的合約地址 (最新部署: 2025-10-08T14:00:00+08:00)。

**網路資訊**：
- **區塊鏈**: BASE Mainnet
- **Chain ID**: 8453
- **區塊瀏覽器**: [BaseScan](https://basescan.org/)
- **起始區塊**: 37392367 (V2.0.0.0 正式部署)
- **上線狀態**: V2.0.0.0 正式版上線，BASE 遷移完成

## 13.2 遊戲核心合約

### 🏰 遊戲核心系統
```bash
# 核心治理合約
🏰 遊戲核心 (DungeonCore): 0xc34fcb2f8d79ec20ebbf6de507ecc8066a8a5ade

# 價格與隨機數服務
💎 價格預言機 (PriceOracle): 0xbf32639c50034833886273d8f9f888e3d819f044
📚 地下城數據 (DungeonStorage): 0xabbb99c1e3d525b39421135845fa609d8bc4b034
```

### 🎮 遊戲功能合約
```bash
# 地下城探險系統
🏛️ 地下城探險 (DungeonMaster): 0xabe0eea017e2689bf85beab6330842010327dbb0

# 英雄升階系統
✨ 英雄升階 (AltarOfAscension): 0xf686f52e5c6121a1ee85e63d38a2b3a5af33b85a
```

## 13.3 NFT 資產合約

### 🦸‍♂️ NFT 資產系統
```bash
# 核心遊戲 NFT
⚔️ 英雄 NFT (Hero): 0x0949742bffade03016e6e0b6f15de138fe6c5e58
🛡️ 神器 NFT (Relic): 0x4ff233dfcb04f27532e0070606310d3dc739c83b

# 組隊系統
👥 隊伍系統 (Party): 0xa096b3f5de84bd51f01acd7ce166d4a02c948406
```

## 13.4 玩家系統合約

### 👤 玩家管理系統
```bash
# 玩家檔案與 VIP 系統
📊 玩家檔案 (PlayerProfile): 0x855bb28f51c5d5088c7a1826d87439011d23dcca
💰 資金庫 (PlayerVault): 0x14c062ddb709f7973ef76e037ae109c85a0c4cb0
🌟 VIP 質押 (VIPStaking): 0xbcbf42f9fbe8efeca66e69d8ce810e12e4221c44

# 隨機數服務
🎲 隨機數管理 (VRFManager): 0x137107f995f2ed9061c1acf01dbe9b06179a90f0
```

## 13.5 代幣系統合約

### 🪙 遊戲代幣
```bash
# 主要遊戲代幣
💎 SOUL 代幣 (SOUL): 0xa5204244859a4f863ece9decb2d222377dc46147

# 穩定幣
💵 USD1 代幣 (USD1): 0x12ea4682604ba45ecbd974fa3baba447f7c641ac
```

**代幣說明**：
- **SOUL**: 正式版遊戲代幣，玩家通過探險獲得的主要獎勵
- **USD1**: 正式版穩定幣，用於價格計算和 VIP 質押

## 13.6 合約功能對照表

### 📋 核心功能映射

| 功能 | 合約名稱 | 地址 | 狀態 |
|------|----------|------|------|
| **英雄鑄造** | Hero | `0x0949742bffade03016e6e0b6f15de138fe6c5e58` | ✅ BASE 運行 |
| **神器鑄造** | Relic | `0x4ff233dfcb04f27532e0070606310d3dc739c83b` | ✅ BASE 運行 |
| **組隊功能** | Party | `0xa096b3f5de84bd51f01acd7ce166d4a02c948406` | ✅ BASE 運行 |
| **地下城探險** | DungeonMaster | `0xabe0eea017e2689bf85beab6330842010327dbb0` | ✅ BASE 運行 |
| **英雄升階** | AltarOfAscension | `0xf686f52e5c6121a1ee85e63d38a2b3a5af33b85a` | ✅ BASE 運行 |
| **VIP 質押** | VIPStaking | `0xbcbf42f9fbe8efeca66e69d8ce810e12e4221c44` | ✅ BASE 運行 |
| **資金管理** | PlayerVault | `0x14c062ddb709f7973ef76e037ae109c85a0c4cb0` | ✅ BASE 運行 |
| **隨機數服務** | VRFManager | `0x137107f995f2ed9061c1acf01dbe9b06179a90f0` | ✅ BASE 運行 |

## 13.7 安全驗證資訊

### 🔒 合約安全特性
- **多重簽名**: 關鍵操作需要多個管理員確認
- **時間鎖**: 重要升級有24-48小時延遲執行
- **緊急暫停**: 發現問題時可立即暫停合約功能
- **重入攻擊防護**: 所有外部調用使用 ReentrancyGuard
- **權限控制**: 使用 OpenZeppelin 的 Ownable 和 AccessControl

### 🔍 合約驗證狀態
- **源碼驗證**: 所有合約源碼已在 BaseScan 上驗證
- **代碼開源**: 完整源碼可在 GitHub 上查看
- **審計狀態**: V2.0.0.0 版本已完成 BASE 遷移並通過安全審查
- **運行狀態**: 合約功能在 BASE 主網穩定運行

## 13.8 開發者資源

### 🛠️ 合約交互工具
- **BaseScan**: 直接在區塊鏈瀏覽器上與合約交互
- **MetaMask**: 使用錢包直接調用合約函數
- **Web3 庫**: 使用 ethers.js 或 viem 進行程式化交互
- **前端介面**: 通過官方遊戲介面進行用戶友好的操作

### 📚 技術文檔
- **ABI 文件**: 所有合約的 ABI 文件已同步到前端專案
- **函數說明**: 詳細的合約函數說明和參數格式
- **事件定義**: 完整的智能合約事件列表
- **整合指南**: 第三方開發者整合指南

## 13.9 網路配置資訊

### 🌐 BASE 主網配置
```javascript
// MetaMask 網路配置
Network Name: Base Mainnet
RPC URL: https://mainnet.base.org
Chain ID: 8453
Currency Symbol: ETH
Block Explorer: https://basescan.org/
```

### 🔗 重要連結
- **官方前端**: [DungeonDelvers 遊戲界面](https://www.dungeondelvers.xyz)
- **BASE 錢包**: [MetaMask BASE 配置指南]
- **交易所**: [Uniswap V3 SOUL/USD 交易對]
- **區塊瀏覽器**: [BaseScan 合約查看](https://basescan.org/)

## 13.10 升級計劃

### 🚀 正式版本路線圖
1. **Phase 1**: 完成最終測試和安全審計
2. **Phase 2**: 部署正式版本合約
3. **Phase 3**: 遷移用戶資料和資產
4. **Phase 4**: 啟動正式版本遊戲

### 📊 V2.0.0.0 BASE 遷移亮點
- **區塊鏈遷移**: 從 BSC 遷移到 BASE Mainnet（更低 Gas 費用、更快確認速度）
- **合約地址更新**: V2.0.0.0 全新部署於 BASE 鏈（所有合約地址已更新）
- **起始區塊**: 37392367（2025-10-27T22:00:00+08:00）全系統一致，子圖與後端已對齊
- **子圖版本**: v2.0.0.0（Goldsky 優先） / v2.0.0.0（The Graph Network）三層備援
- **系統重點**: BASE 原生 ETH 支付、Chainlink VRF V2+ 整合、優化經濟模型

### ⏰ 發展里程碑
- **V1.x BSC 測試**: 2025 Q3 全部完成
- **V2.0.0.0 BASE 遷移**: 2025-10-27 ✅ 成功遷移（主網穩定運行）
- **持續優化**: 2025 Q4 性能監控與改進
- **下一階段內容更新**: 預計 2025 Q4 ~ 2026 Q1

---

> **⚠️ 正式聲明**：以上所有合約地址為 V2.0.0.0 BASE 正式部署版本，請以官方公告為準並避免與來路不明的合約互動。

**技術支援**: 如需技術協助或合約交互指導，請參考官方技術文檔或聯絡開發團隊。
**安全提醒**: 請始終通過官方渠道驗證合約地址的真實性，謹防釣魚攻擊。
**區塊鏈瀏覽器**: 所有合約可在 [BaseScan](https://basescan.org/) 上查看和驗證。
