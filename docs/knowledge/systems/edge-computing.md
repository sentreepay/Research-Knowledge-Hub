---
title: "Edge Computing（邊緣運算）"
category: "Internet of Things"
tags:
  - "IoT"
  - "IoT-Edge-Cloud"
  - "Low Latency"
---

# Edge Computing（邊緣運算）

## 1. 基本概念

邊緣運算（Edge Computing）將運算、儲存或網路服務部署在靠近資料來源的位置，例如邊緣伺服器、基地台、路由器或具備運算能力的設備，以減少資料往返遠端雲端的需求。

## 2. 核心原理

在 IoT-Edge-Cloud 架構中，IoT 裝置收集資料及執行簡單運算；Edge 可就近處理較重視即時性的工作；Cloud 提供較大量的運算與儲存資源，支援複雜分析及長期資料管理。任務可依需求與可用資源在各層間卸載。

## 3. 主要特色

- 將部分處理能力移近資料產生位置。
- 可與雲端協同運算，而非必須取代雲端。
- 需考量節點資源、連線狀況、任務優先權及服務需求。

## 4. 應用情境

可應用於時間敏感的 IoT 服務。邊緣運算回顧論文以智慧醫療說明穿戴式感測資料先送至附近邊緣設備進行即時監測與異常警示，複雜分析及長期儲存則交由雲端。

## 5. 優點與限制

**優點：** 在適當的網路及工作負載條件下，可減少資料傳輸距離並支援較即時的區域處理。

**限制：** 邊緣設備的運算及儲存資源仍有限；高負載可能造成排隊或過載。資料傳輸成本、網路狀態、設備異質性、互通性及安全與隱私亦須納入系統設計。

## 6. 相關論文

- [Meeting the Requirements of Internet of Things: The Promise of Edge Computing](../../papers/meeting-iot-requirements-edge-computing.md)

## 7. 相關知識

- [Task Offloading（任務卸載）](task-offloading.md)
