---
title: "Knowledge Distillation-Based AIoT Framework for Efficient Wireless Gesture Sensing in B5G/6G Networks"
authors: []
year: 2025
publication: "IEEE（刊物名稱待補充）"
paper_url: "https://ieeexplore.ieee.org/document/11017622"
research_area:
  - "AIoT"
  - "Wireless Sensing"
  - "Deep Learning"
tags:
  - "Knowledge Distillation"
  - "Wi-Fi CSI"
  - "Gesture Recognition"
  - "B5G/6G"
status: completed
---

# Knowledge Distillation-Based AIoT Framework for Efficient Wireless Gesture Sensing in B5G/6G Networks

> **中文名稱：** 基於知識蒸餾的 AIoT 框架：用於 B5G/6G 網路高效無線手勢感測  
> **發表資訊：** IEEE，2025；刊物名稱及作者待補充。  
> **論文連結：** [IEEE Xplore](https://ieeexplore.ieee.org/document/11017622)

## 1. 概述

本文探討以知識蒸餾（Knowledge Distillation, KD）壓縮 Wi-Fi 通道狀態資訊（Channel State Information, CSI）手勢與人體活動辨識模型，目標是在資源受限的邊緣裝置上維持辨識能力並降低推論負擔。研究採用 Teacher-Student 架構，結合輸出機率的 Response-based KD 與中間特徵的 Feature-based KD，並在 Raspberry Pi 4 上測試學生模型。

依實驗章節，學生模型在 SignFi 居家與實驗室環境的準確率分別為 98% 與 99.5%，在 HAR 資料集為 94.1%；參數量較比較模型減少約 65%。

## 2. 研究背景

Wi-Fi CSI 描述無線通道特性，包含振幅與相位。人體動作造成的反射、繞射及吸收會改變訊號，因此可分析 CSI 序列辨識手勢與活動。相較攝影機或穿戴式感測器，無線感測可在不直接拍攝或要求使用者配戴裝置的情況下收集動作資訊，心得指出其具有低成本及隱私方面的優點。

大型深度學習模型雖可擷取 CSI 特徵，卻可能需要較多運算、記憶體與電力，不易直接部署於邊緣 IoT 裝置。研究關注如何降低模型複雜度並盡量維持辨識準確率，以及壓縮程度與邊緣裝置即時效能之間的取捨。心得亦指出資料收集條件、使用者動作習慣及環境變化可能造成資料分布差異，影響實際辨識能力。

## 3. 相關工作

心得整理的 Wi-Fi CSI 研究涵蓋 SignFi 手勢辨識，以及使用 1D-CNN、LSTM、GRU 和 Bi-LSTM 擷取訊號局部或時間特徵的方法。較大型或雙向模型可能提高計算負擔，不利於資源有限的裝置。

傳統知識蒸餾多使學生模型模仿教師模型的輸出機率；本研究心得指出，若只使用輸出，可能無法保留教師模型中間層的特徵資訊。因此，該研究結合輸出機率與中間特徵的蒸餾方式。

## 4. 解決方案

研究採用離線 Teacher-Student 流程：先以標記資料訓練教師模型，再利用教師模型輸出與中間特徵訓練較輕量的學生模型。

心得記載教師模型以分類交叉熵（Categorical Cross-Entropy）訓練，並提供分類機率與中間層特徵作為學生模型的學習訊號。

### CSI 前處理

心得記載，研究從 90 個子載波中選取變異數最高的 3 個，串接其振幅與相位，形成 `(timestep, 6)` 輸入；SignFi 的 timestep 為 200，HAR 為 1601。前處理亦提及相位校正及降噪。心得列出 Atheros CSI、Linux 802.11n CSI、Nexmon CSI 及 ESP32 CSI Tool 等 CSI 擷取工具，並記載資料集使用 Intel WiFi Link 5300 收集。

### 聯合知識蒸餾

- **Response-based KD：** 讓學生模型學習教師模型輸出的 Soft Targets，以保留類別機率分布資訊。
- **Feature-based KD：** 比較教師與學生模型 Bottleneck Layer 的輸出，利用特徵匹配損失使中間表示接近。
- **Joint Loss：** 結合分類損失與以 L2 Norm 計算的特徵匹配損失，並以 λ1、λ2 控制各項權重。

心得描述的學生模型以多個平行卷積分支擷取 CSI 特徵，透過元素相加整合至 Bottleneck Layer，再經 Pooling、Flattening 與 Dense Layer 分類；卷積層使用 ReLU，輸出層使用 Softmax。研究亦調整卷積分支及 Dense Layer 神經元數量，觀察模型規模與辨識表現。

## 5. 實驗設計

### 資料集與設定

心得記載研究使用 SignFi 與 Human Activity Recognition（HAR）兩個公開 Wi-Fi CSI 資料集。SignFi 用於手勢辨識，記載包含 276 種手勢、5 位使用者、居家與實驗室兩種環境及 8,280 筆樣本；HAR 用於辨識行走、坐下、站立及跌倒等活動。訓練使用 TensorFlow、Intel i7 CPU、NVIDIA RTX 3050 GPU、Adam Optimizer（學習率 10⁻³）及 Early Stopping。

### 比較與結果

心得記載研究比較 Response-based KD、Feature-based KD、兩者組合及不同標籤訓練方式，並與 1D-CNN、LSTM、GRU、Bi-LSTM 比較。實驗章節記錄 Joint KD 效果較佳；學生模型在 SignFi 居家與實驗室的準確率分別為 98% 與 99.5%，模型大小為 0.108 MB；HAR 準確率為 94.1%，參數量較比較模型減少約 65%。

### 邊緣部署

學生模型部署於 Raspberry Pi 4（2 GB RAM）進行推論，心得記載每筆樣本推論時間約為 6.57–6.64 毫秒。

> **資料註記：** 原心得「概述」另將 SignFi 準確率記為 94.1%；本頁以較詳細的實驗章節為準，採用 SignFi 居家／實驗室 98%／99.5%，HAR 94.1%。若作正式引用，仍建議核對論文原文。

## 6. 結論

依心得整理，研究以輸出蒸餾及特徵蒸餾的聯合設計，將教師模型知識轉移至輕量學生模型，並以 Raspberry Pi 推論測試評估邊緣部署可行性。心得指出模型參數、模型大小及推論時間有所降低，同時維持資料集上的辨識表現。

心得提出的限制包括資料涵蓋的使用者及室內環境有限，且使用者移動、障礙物及無線干擾可能影響 CSI 特徵。未來方向包括大型無線模型、Temporal Attention、Transformer、CSI Doppler Spectrum Analysis，以及整合動作感測器。這些是心得所整理的研究方向，不應視為已由本研究實驗驗證的結果。

## References

- [IEEE Xplore 論文頁面](https://ieeexplore.ieee.org/document/11017622)
