---
title: "Deep Reinforcement Learning for Online Resource Allocation in Network Slicing"
authors: []
year: 2024
publication: "IEEE"
paper_url: "https://ieeexplore.ieee.org/document/10302364"
research_area:
  - "Network Slicing"
  - "Deep Reinforcement Learning"
  - "Resource Allocation"
tags:
  - "PW-DRL"
  - "TRPO"
  - "Lyapunov Optimization"
  - "LSTM"
  - "RAN Slicing"
status: completed
---

# Deep Reinforcement Learning for Online Resource Allocation in Network Slicing

> **中文名稱：** 深度強化學習在網路切片中的線上資源分配之應用  
> **發表資訊：** IEEE，2024（依原心得紀錄）  
> **論文連結：** [IEEE Xplore](https://ieeexplore.ieee.org/document/10302364)

## 1. 概述

本研究針對無線電存取網路（Radio Access Network, RAN）切片中的線上資源分配問題，提出 Prediction-Aided Weighted Deep Reinforcement Learning（PW-DRL）。研究關注在網路資源有限、使用者需求持續變動的情況下，如何動態決定是否接受服務請求，以及如何分配傳輸功率，以提升資源使用效率並維持系統長期穩定。

PW-DRL 將資源分配拆分為使用者請求接受決策與傳輸功率分配兩個子問題，分別整合 Trust Region Policy Optimization（TRPO）與 Lyapunov Optimization；另外加入預測網路，讓決策可參考未來需求及系統狀態資訊。

## 2. 研究背景

隨著 5G 與未來通訊服務發展，同一個實體網路需要支援 4K 影音串流、自動駕駛、智慧電網及遠端手術等不同服務。各服務對傳輸速率、延遲與可靠性的要求不同，傳統以單一方式分配資源的架構較難同時滿足這些需求。

網路切片（Network Slicing）可在同一實體網路設施上建立多個虛擬網路切片，使不同服務依其需求使用網路資源。其中 RAN 切片負責連接使用者設備與網路，並依使用者請求分配無線資源。其挑戰包括：

1. **使用者需求具動態性：** 請求隨時間隨機到達，使用資源的數量與持續時間也不同，可用資源總量不斷變化。
2. **服務需求與優先順序不同：** 不同服務對傳輸速率、延遲及資源使用方式有不同要求。
3. **資源分配具有長期限制：** 除了當下資源限制，也必須考量長期傳輸功率與系統穩定性。
4. **即時最佳化具有計算負擔：** 若每次狀態改變都重新求解最佳化問題，可能需要大量運算時間。

因此，研究希望建立能因應動態需求、兼顧即時決策與長期穩定性的資源分配方法。

## 3. 相關工作

作者將既有網路資源分配研究概分為傳統最佳化方法與機器學習方法。

### 3.1 傳統最佳化方法

過去研究使用凸最佳化、基因演算法（Genetic Algorithm, GA）及其他迭代式搜尋方法，透過數學模型或搜尋程序尋找符合資源限制的分配方案。不過，當網路參數改變時，通常需要重新執行最佳化程序；部分方法也需要大量迭代，因而可能難以符合動態環境中的即時需求。

### 3.2 機器學習方法

相關研究曾使用 GAN-DDQN、LSTM-A2C 及 Q-Learning 等方法處理頻寬、運算資源與網路切片分配。這類方法可學習環境狀態與決策之間的關係，但仍須面對需求變化、長期資源限制及不同服務時間尺度等問題。

### 3.3 本研究的切入點

本研究進一步考量服務請求的持續時間、服務優先順序，以及可用資源隨時間變化的情況。作者認為只依據目前狀態決策，可能無法充分掌握未來網路需求，因此加入預測網路，將未來狀態資訊提供給強化學習模型。其設計整合深度強化學習、Lyapunov Optimization 與預測網路，以同時考量當下需求及長期系統穩定性。

## 4. 解決方案

研究提出 Prediction-Aided Weighted Deep Reinforcement Learning（PW-DRL），將原本的資源分配問題拆分為請求接受決策與傳輸功率分配兩個子問題，並透過不同方法交替求解。

### 4.1 動態 RAN 切片模型

研究將網路服務分為三種類型：

- **Throughput-Oriented（TO）：** 吞吐量導向服務，重視較高資料傳輸速率，請求可能持續占用資源數個 Transmission Time Interval（TTI）。
- **Delay-Sensitive（DS）：** 延遲敏感服務，對延遲要求較高，因此具有較高服務優先順序。
- **Delay-Throughput-Tolerant（DTT）：** 可容忍延遲與吞吐量需求的服務，其使用者請求通常只占用一個 TTI。

### 4.2 使用者請求接受決策：TRPO

研究使用 Trust Region Policy Optimization（TRPO）學習是否接受不同類型的使用者請求。模型需要在接受新請求所帶來的收益，以及可能造成的資源限制違反之間取得平衡。

### 4.3 傳輸功率分配：Lyapunov Optimization

傳輸功率分配使用 Lyapunov Optimization，透過建立虛擬佇列（Virtual Queues），將長期傳輸功率限制轉換為可逐步處理的最佳化問題。如此可將長期穩定性要求納入每個時間點的資源分配決策，而不只追求當下效能。

### 4.4 預測網路

預測網路分為 Online 與 Offline 兩個部分：

- **Online Prediction：** 使用長短期記憶網路（LSTM）預測下一個 TTI 的 DTT 使用者請求，讓系統提前掌握即將到來的需求。
- **Offline Prediction：** 結合 LSTM 與一維卷積神經網路（1D-CNN）預測未來系統狀態，並將預測結果提供給強化學習模型作為決策參考。

透過預測網路，TRPO 除了目前環境狀態，也能參考未來可能的變化。整體而言，PW-DRL 並非單一全新的強化學習演算法，而是整合 TRPO、Lyapunov Optimization 與預測網路的資源分配架構，分別處理請求接受、功率分配及未來狀態預測。

## 5. 實驗設計

### 5.1 實驗環境

作者透過模擬環境驗證 PW-DRL 在不同可用資源數量下處理動態使用者請求及維持長期系統穩定性的能力。實驗比較每個 TTI 可使用 300 與 500 個 Resource Units 的情境。

### 5.2 比較方法

比較方法包含 Actor-Critic（AC）、TRPO、Soft Actor-Critic（SAC）、Random Action、移除預測網路的 S-PW-DRL，以及 Genetic Algorithm（GA）、Pattern Search（PS）與 Genetic Algorithm for Multi-Objective（GMAO）。藉此比較不同強化學習方法、傳統最佳化方法，以及預測網路對整體效能的影響。

### 5.3 評估指標

- **Reward：** 衡量資源分配過程取得的獎勵，反映整體決策效能。
- **Convergence：** 觀察模型訓練是否穩定收斂。
- **Average Number of TTIs before Constraints Violated：** 衡量系統在違反限制條件前，平均可維持的 TTI 數量。
- **Throughput：** 衡量成功接受的使用者請求所產生的平均資料傳輸量。
- **Acceptance Ratio：** 衡量不同類型使用者請求被接受的比例。

### 5.4 實驗結果

依原心得整理，PW-DRL 在不同資源條件下皆取得較好的長期獎勵與收斂表現。當每個 TTI 僅有 300 個 Resource Units 時，部分其他強化學習方法的表現明顯下降，甚至無法順利收斂，顯示 PW-DRL 在資源較受限的情境中仍有較好的適應能力。

S-PW-DRL 與 TRPO 的比較顯示，加入 Lyapunov Optimization 後，系統穩定性有所改善；完整 PW-DRL 又優於移除預測網路的 S-PW-DRL，顯示預測網路提供的未來狀態資訊有助於決策。PW-DRL 在 300 與 500 個 Resource Units 的情境下，皆能維持較長運作時間並取得較佳平均吞吐量。

不同服務類型的接受率方面，DS 最高，與其服務優先權較高及訓練時被賦予較大權重有關；DTT 接受率高於 TO，因為 TO 通常會持續占用數個 TTI 且需要較多資源。原心得亦提醒，傳統最佳化方法的比較未納入長期限制條件，因此解讀比較結果時需留意此差異。

## 6. 結論

本研究針對 5G RAN 切片中的動態資源分配問題，提出整合深度強化學習、最佳化方法與預測網路的 PW-DRL 架構。研究將資源分配拆成使用者請求接受決策與傳輸功率分配兩個子問題，分別使用 TRPO 與 Lyapunov Optimization 處理，並透過 LSTM、1D-CNN 組成的預測網路提供未來需求及系統狀態資訊。

依原心得整理，PW-DRL 在不同資源條件下展現良好效能，尤其在資源有限時仍能維持較高長期獎勵與較佳系統穩定性。研究也指出，Lyapunov Optimization 與預測網路的加入，對整體資源分配表現有正面幫助。

研究限制包括：主要以模擬環境驗證，尚未在真實網路環境部署；離線訓練仍需一定計算成本；兩個子問題採交替求解，無法在理論上保證整體方法一定取得最佳解；若實際環境與訓練資料分布不同，也可能影響泛化能力。

## References

- [IEEE Xplore 論文頁面](https://ieeexplore.ieee.org/document/10302364)

> **整理說明：** 本頁依據既有論文心得轉寫，未在心得未提供處補入實驗數值或作者資訊；若要引用精確數據，請再核對論文原文。
