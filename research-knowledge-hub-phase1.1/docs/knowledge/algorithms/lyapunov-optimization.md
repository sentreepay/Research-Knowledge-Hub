---
title: "Lyapunov Optimization（李雅普諾夫最佳化）"
category: "Optimization"
tags: ["Long-term Constraints", "Virtual Queue", "Resource Allocation"]
---

# Lyapunov Optimization（李雅普諾夫最佳化）

## 1. 基本概念

Lyapunov Optimization 是一類處理動態系統長期效能與穩定性問題的最佳化方法，常用於資源分配、排程及網路控制。它將長期限制轉換成可隨時間逐步處理的決策問題。

## 2. 核心原理

常見作法是建立虛擬佇列（Virtual Queues），讓佇列累積狀態代表長期限制是否被遵守，再透過控制佇列漂移與當下效能之間的權衡，形成每個時間點可執行的決策。

## 3. 主要特色

- 適合動態到達、狀態隨時間改變的系統。
- 可將長期平均限制轉化為線上決策問題。
- 透過虛擬佇列追蹤限制條件。
- 可與學習式決策方法搭配。

## 4. 應用情境

常見於通訊網路資源管理、能源管理及排程問題。在網路切片論文中，該方法用於傳輸功率分配，將長期功率限制納入每個時間點的決策。

## 5. 優點與限制

**優點：** 不必每次都重新求解完整的長期規劃問題，適合線上、動態決策。

**限制：** 效能與穩定性取決於系統模型、參數設定及佇列設計；方法本身也不代表所有情境下都能取得全域最佳解。

## 6. 相關論文

- [Deep Reinforcement Learning for Online Resource Allocation in Network Slicing](../../papers/deep-reinforcement-learning-network-slicing.md)

## 7. 相關知識

- [Trust Region Policy Optimization（TRPO）](trpo.md)
