# 11. 技術架構總覽 (Technical Architecture Overview)

> **V1.0 第一代遊戲技術架構** - 2025年9月更新

## 11.1 專案架構模式 (Project Architecture Pattern)

**Soulbound Saga** 採用微服務架構模式，將不同功能模組分別部署和管理，實現高度的可擴展性和維護性。

### 🏗️ 核心組件架構

```
🎮 DungeonDelvers 生態系統
├── 🌐 前端應用 (SoulboundSaga)
├── 🔗 智能合約層 (DungeonDelversContracts)
├── 📊 數據索引層 (dungeon-delvers-subgraph)
├── 🚀 後端 API (dungeon-delvers-metadata-server)
└── 📚 文檔系統 (dungeon-delvers-whitepaper)
```

## 11.2 各子專案詳細說明

### 🌐 前端應用 - SoulboundSaga
**技術棧**: React 18 + TypeScript + Vite + wagmi v2  
**專案位置**: `/Users/sotadic/Documents/GitHub/SoulboundSaga`  
**部署**: Vercel  

**核心功能**:
- Web3 錢包連接與交互
- NFT 展示和交易界面  
- 遊戲機制操作 (鑄造、探索、升級)
- 實時數據展示和統計分析
- 響應式設計和手機端優化

**技術亮點**:
```typescript
// 統一配置管理系統
const contracts = await loadContractsFromCDN();

// 現代化 Web3 集成
const { writeContract } = useWriteContract();
await writeContract({
  address: contracts.HERO_ADDRESS,
  abi: HeroABI,
  functionName: 'mint'
});
```

### 🔗 智能合約層 - DungeonDelversContracts  
**技術棧**: Solidity + Hardhat + OpenZeppelin  
**專案位置**: `/Users/sotadic/Documents/DungeonDelversContracts`  
**網路**: BNB Chain (BSC) Mainnet  

**核心合約**:
```solidity
// 核心 NFT 合約
SoulDelver.sol     // 探索者 NFT
SoulRelic.sol      // 魂器 NFT  
DelverSquad.sol    // 探索小隊 NFT
VIPCard.sol        // VIP 會員卡 NFT

// 遊戲邏輯合約
DungeonMaster.sol  // 地城探索主合約
SoulVault.sol      // 智能金庫
VRFManager.sol     // Chainlink VRF 隨機數
```

**安全特性**:
- Chainlink VRF V2.5 保證隨機公平性
- 多重簽名和時間鎖機制
- ReentrancyGuard 防重入攻擊
- Ownable 權限控制系統

### 📊 數據索引層 - dungeon-delvers-subgraph
**技術棧**: The Graph Protocol + GraphQL  
**專案位置**: `/Users/sotadic/Documents/GitHub/dungeon-delvers-subgraph`  
**版本**: v1.4.0.3  

**索引數據**:
```graphql
type Player {
  id: ID!
  heroes: [Hero!]! @derivedFrom(field: "owner")
  relics: [Relic!]! @derivedFrom(field: "owner") 
  totalMinted: BigInt!
  lastActivity: BigInt!
}

type Hero {
  id: ID!
  tokenId: BigInt!
  owner: Player!
  rarity: Int!
  level: Int!
  experience: BigInt!
}
```

**查詢能力**:
- 實時 NFT 數據同步
- 用戶資產查詢和統計
- 遊戲事件歷史追蹤
- 排行榜和分析數據

### 🚀 後端 API - dungeon-delvers-metadata-server
**技術棧**: Node.js + Express.js + ethers.js  
**專案位置**: `/Users/sotadic/Documents/dungeon-delvers-metadata-server`  
**版本**: v1.4.0.3  
**部署**: Render  

**API 端點設計**:
```javascript
// NFT Metadata 服務
GET /metadata/:type/:id

// 系統健康檢查  
GET /health
GET /api/config/status
GET /admin/cache-stats

// 配置管理
POST /api/config/refresh
```

**核心特性**:
- 動態 NFT metadata 生成（純子圖資料來源，零 RPC 成本）
- SVG 圖像實時渲染
- 多層緩存策略 (記憶體 + CDN) 與事件觸發式刷新
- 統一配置管理（支援 `config/contracts.json` 與環境變數覆寫）
- Goldsky / The Graph 自動切換機制與健康快照 (`/health` 回傳 `subgraphEndpoints`)
- 高可用性與速率限制、Helmet 安全強化

### 📚 文檔系統 - dungeon-delvers-whitepaper  
**技術棧**: GitBook + Markdown  
**專案位置**: `/Users/sotadic/Documents/GitHub/dungeon-delvers-whitepaper`  
**版本**: V1.0 第一代遊戲  

**文檔結構**:
- 專案概述和遊戲機制
- 技術架構和智能合約
- 代幣經濟學和 NFT 系統
- 開發指南和 API 文檔

## 11.3 數據流架構 (Data Flow Architecture)

### 🔄 用戶操作流程
```mermaid
graph TD
    A[用戶錢包] --> B[前端界面]
    B --> C[智能合約]
    C --> D[區塊鏈事件]
    D --> E[子圖索引]
    E --> F[GraphQL API]
    F --> B
    
    C --> G[後端 API]
    G --> H[Metadata 服務]
    H --> B
```

### 📡 配置同步系統
```bash
# 統一配置管理流程
DungeonDelversContracts/config/deployed-addresses.mainnet.json
├─ scripts/essential/extract-abis.js → SoulboundSaga/src/contracts/abi
│                                     ↳ dungeon-delvers-metadata-server/abis
├─ dungeon-delvers-subgraph/scripts/sync-subgraph-manifest.cjs → subgraph.yaml
└─ metadata-server/config/contracts.json  # 統一配置載入器依此覆寫
```

## 11.4 部署和 CI/CD 策略

### 🚀 部署環境
- **前端**: Vercel (自動部署)
- **後端**: Render (容器化部署)  
- **子圖**: The Graph Studio (去中心化索引)
- **智能合約**: BNB Chain (永久部署)

### 🔄 持續集成流程
```yaml
# GitHub Actions Workflow
- Code Push → Automated Tests
- Tests Pass → Build & Deploy  
- Deploy Success → Configuration Sync
- Sync Complete → Health Checks
```

## 11.5 安全和監控系統

### 🛡️ 安全措施
- **智能合約**: 多重簽名 + 時間鎖
- **API 服務**: CORS + 速率限制 + Helmet 安全頭
- **數據傳輸**: HTTPS + CSP 策略
- **錢包集成**: 官方 wallet 連接器

### 📊 監控和告警
```javascript
// 健康檢查系統
{
  "frontend": "https://dungeondelvers.xyz/health",
  "backend": "https://api.dungeondelvers.xyz/health", 
  "subgraph": "https://api.studio.thegraph.com/...",
  "contracts": "BSCScan API monitoring"
}
```

## 11.6 性能優化策略

### ⚡ 前端優化
- **代碼分割**: React.lazy + Suspense
- **圖像優化**: WebP + 懶加載
- **緩存策略**: Service Worker + CDN
- **Bundle 分析**: Rollup Visualizer

### 🔧 後端優化  
- **API 緩存**: 5分鐘內存緩存
- **數據壓縮**: gzip 壓縮傳輸
- **連接池**: 數據庫連接復用
- **負載均衡**: 多實例部署

### 📈 區塊鏈優化
- **Gas 優化**: 批量操作 + 狀態壓縮
- **事件索引**: 高效的 GraphQL 查詢
- **VRF 優化**: Direct Funding 模式
- **交易排隊**: 智能 Gas 價格策略

## 11.7 擴展性設計

### 🌟 水平擴展能力
- **微服務架構**: 各組件獨立擴展
- **API 網關**: 統一入口和負載分散
- **數據庫分片**: 用戶數據水平分割
- **CDN 分發**: 全球內容分發網路

### 🔮 未來技術升級
- **Layer 2 集成**: Polygon, Arbitrum 支援
- **跨鏈橋接**: 多鏈資產互操作性
- **AI 增強**: 智能遊戲平衡和推薦
- **VR/AR 集成**: 沉浸式遊戲體驗

---

> **💡 開發者注意**: 此架構文檔會隨著 V1.0 第一代遊戲的發展持續更新。所有技術決策都以用戶體驗和系統穩定性為優先考量。

**最後更新**: 2025年9月2日  
**架構版本**: V1.0 第一代遊戲  
**維護團隊**: DungeonDelvers 開發團隊
