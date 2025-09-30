# 14. V1.4.0.3 版本更新摘要

> 更新日期：2025-09-25 ｜ 對應主網部署：BSC `62385903+`

## 亮點
- **全新合約組**：Hero、Relic、Party、PlayerVault、VIPStaking 等核心合約全面升級，地址已在合約倉庫及 README 中同步。
- **VRF 架構升級**：導入 `VRFConsumerV2Plus`，遠征結果改採訂閱模式並新增冷卻事件 `PartyCooldownUpdated`。
- **金庫與稅制優化**：PlayerVault 支援小額免稅、稅率階梯與推薦佣金追蹤，提供 `/admin/cache-stats` 用於監控。
- **升階機制調整**：AltarOfAscension 增加材料鎖定保護與 VRF 錯誤降級路徑，升階結果透過 `UpgradeRevealed` 暴露。
- **VIP 等級上限提升**：VIPStaking 改為 `sqrt(USD/100)` 計算，最高等級提高至 20，並加入緊急模式。

## 開發者須知
1. **前端**：改用 `docs/api/hooks-api-reference.md` / `components-api-reference.md` 管理 UI 與資料管線，子圖陣列備援已可移除。
2. **子圖**：`schema.graphql` 新增預計算欄位 `heroCount`、`relicCount`、`partyCount`，請使用 `docs/GRAPHQL_QUERY_EXAMPLES.md` 中的新版查詢。
3. **後端**：Metadata Server 以純子圖模式運作，所有快取與健康報告已整理至 `docs/BACKEND_SPEC.md`。
4. **合約**：ABI 發佈流程統一由 `node scripts/essential/extract-abis.js` 完成；請勿再使用過時的 `ultimate-config-system.js`。
5. **白皮書**：本版本將 Tokenomics 地址更新為正式 SOUL 合約，並新增本頁作為版本紀錄。

## 檢查清單
- [ ] 更新 `.env` 與部署腳本中的合約地址
- [ ] 重新部署並驗證子圖 (`npm run build && npm run deploy`)
- [ ] 後端重啟並執行 `npm run lint`, `npm run test`
- [ ] 前端執行 `npm run type-check`, `npm run lint`, `npm run test`
- [ ] 對外公告：VIP 等級上限、新地址、升階規則

---
更多細節請參考各倉庫的 `DOCUMENTATION_INDEX.md` 與專案 SPEC。
