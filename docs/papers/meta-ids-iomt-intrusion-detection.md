---
title: "Meta-IDS: Meta-Learning-Based Smart Intrusion Detection System for Internet of Medical Things (IoMT) Network"
authors: []
year: 2024
publication: "IEEE"
paper_url: "https://ieeexplore.ieee.org/document/10496441"
research_area:
  - "Cybersecurity"
  - "Intrusion Detection"
  - "Internet of Medical Things"
tags:
  - "Meta-Learning"
  - "IoMT"
  - "Zero-day Attack"
  - "XGBoost"
  - "Anomaly Detection"
status: completed
---

# Meta-IDS: Meta-Learning-Based Smart Intrusion Detection System for Internet of Medical Things (IoMT) Network

> **中文名稱：** Meta-IDS：基於元學習的醫療物聯網（IoMT）網路智慧入侵偵測系統  
> **發表資訊：** IEEE，2024（依原心得紀錄）  
> **論文連結：** [IEEE Xplore](https://ieeexplore.ieee.org/document/10496441)

## 1. 概述

本研究提出基於元學習（Meta-learning）的智慧入侵偵測系統 Meta-IDS，應用於醫療物聯網（Internet of Medical Things, IoMT）網路環境，目標是提升已知攻擊與零日攻擊（Zero-day Attacks）的偵測能力。

Meta-IDS 結合監督式與非監督式學習，包含兩個主要偵測機制：一是基於特徵的入侵偵測（Signature-based IDS），使用多種機器學習與元學習架構辨識已知攻擊；二是基於異常的入侵偵測（Anomaly-based IDS），使用 Mean Shift Clustering 與偏差分類器（Biased Classifiers）辨識未知零日攻擊。此外，研究使用 Bat Algorithm 與 BO-TPE 進行超參數最佳化。

## 2. 研究背景

IoMT 將物聯網技術應用於醫療照護，透過醫療感測器與網路設備蒐集、傳輸患者生理資訊，例如心率、體溫及心電圖，支援健康監測與遠端醫療服務。然而，設備間的網路連線也可能遭受攻擊，造成敏感醫療資料外洩，甚至影響患者安全。

研究心得列舉的攻擊類型包括：

- **DoS（Denial of Service）：** 透過大量請求使系統無法正常運作。
- **MITM（Man-in-the-Middle）：** 攔截或竄改雙方傳輸的資料。
- **Data Injection：** 將惡意資料注入系統。
- **Spoofing：** 偽造身分或資料來源。

傳統入侵偵測主要有兩種方式。特徵式偵測依已知攻擊特徵或規則比對，能辨識已知攻擊，但難以發現尚未建立特徵的新型攻擊；異常式偵測建立正常網路行為模式，找出偏離模式的資料，但可能產生誤判。此外，IoMT 設備通常受到運算能力與儲存空間限制，因此偵測系統也需要考量執行時間及資源效率。

本研究關注如何同時辨識已知攻擊與未知零日攻擊、整合多種模型以降低單一分類器限制、降低誤報與漏報，以及兼顧 IoMT 環境的即時性需求。

## 3. 相關工作

### 3.1 傳統機器學習與深度學習方法

既有 IoT 與 IoMT 入侵偵測研究曾使用決策樹（Decision Tree）、隨機森林（Random Forest）、LSTM、CNN 與集成學習（Ensemble Learning）。這些方法可用於攻擊分類或網路流量特徵學習，但其表現可能受到資料特性、模型複雜度及未知攻擊影響。

### 3.2 現有研究的不足

原心得整理的限制包括：傳統特徵式 IDS 依賴已知攻擊特徵；部分深度學習模型運算成本較高，可能不適合資源有限的 IoMT 設備；集成學習仍需改善未知攻擊辨識；異常偵測可能產生誤報與漏報；部分研究對醫療敏感資料及跨領域應用的考量不足。

### 3.3 本研究與過去研究的差異

本研究並非只使用單一模型分類攻擊，而是將多種演算法整合至同一架構：使用多個弱學習器（Weak Learners）並以 XGBoost 作為元學習器（Meta Learner）；使用 Bat Algorithm 與 BO-TPE 進行超參數最佳化；再結合 Mean Shift Clustering 與偏差分類器，補足監督式學習對未知攻擊偵測的不足。

## 4. 解決方案

Meta-IDS 主要由資料前處理、特徵工程、元學習及異常偵測四個部分組成。

### 4.1 資料前處理

研究使用 SMOTE（Synthetic Minority Over-sampling Technique）處理類別不平衡問題，透過少數類別樣本生成合成資料，使正常與攻擊資料的比例更平衡。此外，使用 Label Encoder 將類別型資料轉為數值，並透過標準化將資料調整為平均值 0、標準差 1，以降低不同特徵尺度的影響。

### 4.2 特徵工程

研究使用兩種方法減少不重要特徵並降低模型運算負擔：

- **RFE（Recursive Feature Elimination）：** 反覆移除重要性較低的特徵，找出對分類有幫助的特徵。
- **LDA（Linear Discriminant Analysis）：** 將高維資料轉換至較低維度空間，同時盡可能保留不同類別之間的區別能力。

### 4.3 元學習架構

研究將模型分成兩個層級。

**第一層：弱學習器（Weak Learners）**。使用決策樹（DT）、隨機森林（RF）、AdaBoost、神經網路（NN）、多層感知器（MLP）及多項式樸素貝葉斯（MNB）作為基礎分類器。各模型分別學習網路流量資料並產生預測結果。

**第二層：元學習器（Meta Learner）**。使用 XGBoost 接收第一層各弱學習器的預測結果，再學習如何整合不同模型的判斷，產生最終分類結果。

研究另使用兩種超參數最佳化技術：Bat Algorithm 模仿蝙蝠回聲定位行為，搜尋弱學習器的超參數組合；BO-TPE（Bayesian Optimization - Tree-structured Parzen Estimator）透過貝葉斯最佳化搜尋元學習器的適當超參數。

### 4.4 零日攻擊偵測

由於元學習架構主要辨識已知攻擊，研究另外設計異常式入侵偵測系統處理未知攻擊，包含：

- **Mean Shift Clustering：** 透過分群分析資料分布與特徵，區分正常行為與可疑攻擊行為，以找出可能的未知攻擊。
- **Biased Classifiers：** 使用兩個以隨機森林為基礎的分類器，分別改善 Mean Shift Clustering 產生的漏報（False Negative）與誤報（False Positive）。當分群結果信心不足時，系統會將可疑資料交由偏差分類器進一步判斷。

## 5. 實驗設計

### 5.1 實驗資料集

研究使用三個公開資料集測試系統在不同 IoT 與醫療物聯網環境中的攻擊偵測能力。

| 資料集 | 資料筆數 | 特徵數量 | 研究用途 |
|---|---:|---:|---|
| WUSTL-EHMS-2020 | 16,138 | 44 | 醫療健康監測環境，包含感測器與網路流量資料 |
| IoTID20 | 625,783 | 80 | IoT 設備網路攻擊偵測 |
| WUSTL-IIOT-2021 | 1,194,464 | 41 | IIoT 環境中的攻擊偵測 |

### 5.2 實驗環境與評估方式

研究使用 Python，搭配 Pandas、Scikit-learn 及 XGBoost 等工具實作模型。資料中 70% 作為訓練集，剩餘 30% 作為測試集，並使用十折交叉驗證（10-fold Cross Validation）評估模型在不同資料子集上的表現。針對未知攻擊，另以保留未知攻擊樣本的方式測試模型辨識新型攻擊的能力。

### 5.3 評估指標

- **Accuracy：** 整體分類正確的比例。
- **Precision：** 被判斷為攻擊的資料中，實際為攻擊的比例。
- **Recall：** 所有實際攻擊資料中，成功偵測的比例。
- **F1-score：** Precision 與 Recall 的調和平均。
- **Execution Time：** 模型完成偵測所需時間。
- **Misclassification Rate：** 錯誤分類率。

其中 Precision 與 Recall 對入侵偵測特別重要，因為系統除了需要正確辨識攻擊，也必須避免漏掉真正的攻擊行為。

### 5.4 實驗結果

**已知攻擊偵測：** 原心得整理的 Meta-IDS 準確率如下。

| 資料集 | 準確率 | 執行時間 |
|---|---:|---:|
| WUSTL-EHMS-2020 | 99.57% | 77.2 秒 |
| IoTID20 | 99.93% | 247.3 秒 |
| WUSTL-IIOT-2021 | 99.99% | 307.3 秒 |

**未知攻擊偵測：** 比較僅使用 Mean Shift 與加入偏差分類器後的準確率。

| 資料集 | 僅使用 Mean Shift | 加入偏差分類器後 |
|---|---:|---:|
| WUSTL-EHMS-2020 | 62.86% | 99.50% |
| IoTID20 | 81.31% | 99.98% |
| WUSTL-IIOT-2021 | 94.68% | 99.99% |

加入偏差分類器後，三個資料集的準確率均明顯提升，顯示其可針對分群模型容易誤判的資料進行額外判斷。

**消融實驗：** 移除元學習器 XGBoost 後，準確率下降。

| 資料集 | 完整模型 | 移除元學習器後 |
|---|---:|---:|
| WUSTL-EHMS-2020 | 99.57% | 98.83% |
| IoTID20 | 99.91% | 98.64% |
| WUSTL-IIOT-2021 | 99.99% | 97.24% |

結果顯示元學習器在整合不同弱學習器預測結果方面具有作用，尤其在 WUSTL-IIOT-2021 資料集上，移除元學習器後的準確率下降較明顯。

## 6. 結論

本研究提出 Meta-IDS，整合機器學習、元學習及異常偵測技術，建立用於 IoMT 的入侵偵測系統。其主要設計包括使用 SMOTE、RFE 與 LDA 改善資料處理及特徵選擇；以六種機器學習模型作為弱學習器，並使用 XGBoost 作為元學習器；透過 Bat Algorithm 與 BO-TPE 進行超參數最佳化；以及結合 Mean Shift Clustering 與偏差分類器提升零日攻擊偵測能力。

依原心得整理，系統在三個公開資料集上，已知攻擊與未知攻擊偵測均展現良好結果。不過，研究仍有環境變化、資料集依賴、新型攻擊持續演變、運算資源需求，以及跨領域擴展等限制。未來方向包括改善異常式入侵偵測、導入更多非監督式學習與進階異常偵測技術，並研究模型在大型 IoT 醫療環境中的擴展能力。

## References

- [IEEE Xplore 論文頁面](https://ieeexplore.ieee.org/document/10496441)

> **整理說明：** 本頁依據既有論文心得轉寫。作者姓名未見於心得資料，因此未自行補入；若要引用精確實驗數值，請再核對論文原文。
