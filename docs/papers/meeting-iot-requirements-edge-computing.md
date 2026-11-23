---
title: "Meeting the Requirements of Internet of Things: The Promise of Edge Computing"
authors: []
year: 2024
publication: "IEEE（刊物名稱待補充）"
paper_url: "https://ieeexplore.ieee.org/document/10342693"
research_area:
  - "Edge Computing"
  - "Internet of Things"
  - "Task Offloading"
tags:
  - "IoT-Edge-Cloud"
  - "Task Offloading"
  - "Resource Management"
  - "Survey"
status: completed
---

# Meeting the Requirements of Internet of Things: The Promise of Edge Computing

> **中文名稱：** 滿足物聯網需求：邊緣運算的願景  
> **發表資訊：** IEEE，2024；刊物名稱及作者待補充。  
> **論文連結：** [IEEE Xplore](https://ieeexplore.ieee.org/document/10342693)

## 1. 概述

本文回顧邊緣運算在物聯網（Internet of Things, IoT）中的任務卸載研究，整理 IoT、Edge 與 Cloud 協同運算的架構、最佳化目標與方法。心得涵蓋水平與垂直卸載、二元與部分卸載、邊緣資源聯盟，以及排隊理論、賽局理論、人工智慧、演化式計算與機率演算法等技術，並以智慧醫療說明各層協同方式。

## 2. 研究背景

IoT 裝置的處理能力、記憶體及電池資源有限；若將所有工作傳送至遠端雲端，資料傳輸距離及網路節點可能增加延遲與能耗。邊緣運算將運算及儲存資源部署在靠近資料來源的位置，以支援時間敏感的服務；但邊緣設備本身也有資源上限，可能遇到任務排隊及設備過載。

因此，任務卸載須在本地、邊緣及雲端運算間安排工作，同時考量執行與傳輸時間、能源消耗、設備能力、網路狀態及服務品質（Quality of Service, QoS）。本文回顧的核心問題是如何選擇卸載時機、方式及目的地，以及現有架構能否兼顧不同 QoS 需求。

## 3. 相關工作

心得記載作者使用 ACM Digital Library、Web of Knowledge、IEEE Xplore 及 ScienceDirect，以 Edge Computing、IoT、Offloading 為關鍵字搜尋 2015–2023 年研究，取得超過 140 篇論文，並比較不同 Survey Paper 對延遲、能源、資源、移動性、成本及 QoS 等面向的涵蓋範圍。

相關研究涵蓋行動邊緣運算、車載邊緣網路、機器學習導向的資料處理、隨機卸載及工作負載分配。心得指出，既有研究常聚焦特定應用或最佳化目標；本文則以 IoT-Edge-Cloud 協同運算的角度整理卸載架構與最佳化方法。此文為文獻回顧，並非提出單一新型卸載演算法。

心得提及 Shakarami 等人對機器學習於行動邊緣運算的整理、Yuan 等人對車載邊緣網路運算效率的研究、Aazam 等人對 IoT 邊緣資料處理的回顧，以及 Mukherjee 等人對觸覺網際網路工作負載分配的探討；另有研究採隨機式卸載策略分析邊緣網路效能與延遲。

## 4. 解決方案

本文依心得整理，可從運算層級、工作分割方式及資源管理方法理解任務卸載。

### IoT-Edge-Cloud 與卸載層級

IoT 層收集資料並進行簡單的本地運算；Edge 層在靠近資料來源的位置處理工作，可依任務優先權及可用資源接收或轉送任務；Cloud 層提供較大量的運算及儲存能力，適合複雜分析及長期資料管理。邊緣運算並非完全取代雲端。

- **水平卸載：** 在相同層級的設備間分配工作，例如 Device-to-Device（D2D）或 Peer-to-Peer（P2P）卸載；可將工作拆為子任務平行執行，心得提到可用有向無環圖（Directed Acyclic Graph, DAG）表示任務關係。
- **垂直卸載：** 將工作從 IoT 裝置移至 Edge 或 Cloud 等不同運算層級。
- **二元卸載：** 將一項任務交由單一運算設備執行，決策較直接，但受單一設備資源限制。
- **部分卸載：** 將任務拆成子任務並分配至多個設備；子任務相依時可能需要等待。部分協同卸載則允許不同服務提供者的邊緣設備分享資源。
- **邊緣資源聯盟：** 以 Resource Controller 協調不同服務提供者的設備資源，在伺服器負載較高時轉移部分工作。

選擇卸載時須將遠端計算時間與資料上傳、結果下載時間一併考量。傳輸資料量大或頻寬不足時，遠端執行不一定比本地執行更快。

### 最佳化目標與方法

心得整理的資源需求包括運算、通訊、感測及語意；語意相關技術列有 RDF、OWL 及 Efficient XML Interchange（EXI）。最佳化目標涵蓋延遲、能源消耗、資源使用率、負載平衡、移動性、優先權、成本、QoS 及安全性等。文中回顧的技術包括：

- **排隊理論：** 以 M/M/1、M/M/c 等模型及 FCFS、LIFO 等規則分析任務到達、服務及等待。
- **賽局理論：** 分析設備或服務提供者的策略互動，用於資源競爭、成本協商及資源共享。
- **人工智慧：** 使用監督式或非監督式學習分析資料；深度強化學習可依據 Agent、State、Action、Reward 逐步調整卸載決策。
- **演化式計算與機率方法：** 心得列舉 Genetic Algorithm、Ant Colony Optimization、Particle Swarm Optimization 及機率演算法，應用於資源配置與卸載搜尋。
- **其他最佳化：** 文中亦提及線性、非線性及動態規劃。

上述為文獻回顧中整理的方法及用途，不代表本文提出或以同一實驗驗證了所有方法。

## 5. 實驗設計

本文屬文獻回顧型研究，沒有自行提出新模型或建立獨立實驗環境。心得記載作者以四個學術資料庫蒐集超過 140 篇 2015–2023 年間的研究，並比較其最佳化目標與技術方法。

心得另整理了深度強化學習的系統獎勵（System Reward）及總執行成本（Total Execution Cost）圖表，但未提供可在此重述的具體數值。智慧醫療案例描述穿戴式感測器將心跳、血壓、體溫及心電圖等資訊送至邊緣設備進行即時監測與異常警示；較複雜分析及長期儲存由雲端處理。心得明確指出此為架構與流程說明，並非臨床試驗。

## 6. 結論

依心得整理，本文將 IoT-Edge-Cloud 協同運算、任務卸載架構及資源管理方法加以分類，並以智慧醫療說明邊緣即時處理與雲端分析的分工。邊緣運算可協助降低資料往返遠端雲端的需求，但成效仍取決於任務、網路及設備條件。

心得列出的待解挑戰包括任務排程與資源需求、應用擴展性、資源配置、設備互通性、6G 通訊技術、IoT 設備異質性，以及安全與隱私保護。文中未提供單一演算法的統一效能結論；各卸載方法仍須依延遲、能源與資源等目標選擇。

## References

- [IEEE Xplore 論文頁面](https://ieeexplore.ieee.org/document/10342693)
