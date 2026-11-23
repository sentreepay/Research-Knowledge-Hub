---
title: "Harnessing Vision-Language Models for Time Series Anomaly Detection"
authors: []
year: 2026
publication: "AAAI"
paper_url: "https://doi.org/10.48550/arXiv.2506.06836"
research_area:
  - "Artificial Intelligence"
  - "Time Series Analysis"
tags:
  - "Time Series Anomaly Detection"
  - "Vision-Language Model"
  - "Zero-shot Learning"
  - "ViT4TS"
  - "VLM4TS"
status: completed
---

# Harnessing Vision-Language Models for Time Series Anomaly Detection

> **中文名稱：** 運用視覺語言模型進行時間序列異常偵測  
> **發表資訊：** AAAI，2026（依原始心得紀錄）  
> **論文連結：** [arXiv / DOI](https://doi.org/10.48550/arXiv.2506.06836)  
> **程式碼：** [VLM4TS GitHub](https://github.com/ZLHe0/VLM4TS)

## 1. 概述

本研究探討如何運用 Vision-Language Models（VLMs）進行時間序列異常偵測（Time Series Anomaly Detection, TSAD）。傳統方法多以數值資料訓練特定領域模型，對時間序列的視覺型態與長距離上下文理解仍有限；直接將時間序列圖表交由 VLM 判讀，也可能面臨準確度、效率及異常邊界定位問題。

論文提出兩階段架構：第一階段 ViT4TS 將時間序列轉為視覺表示並篩選候選異常區間；第二階段 VLM4TS 使用 VLM 檢查候選區間、移除誤報並補充可能遺漏的異常。

## 2. 研究背景

時間序列可能具有不同時間尺度與動態行為，系統必須區分真正異常與正常波動。例如，某些數值突然上升可能是歷史上反覆出現的正常現象；相對地，緩慢偏離既有趨勢也可能代表異常。

既有方法常依賴特定領域假設或訓練資料。將長序列輸入 VLM 時，亦存在兩種取捨：

1. **短上下文：** 將長序列切成多個小視窗，可能增加 Token 成本與推論延遲，也不易掌握長距離關係。
2. **長上下文：** 將完整序列繪製成單張圖，可能降低解析度，使模型難以精確定位異常邊界。

## 3. 相關工作

原始心得將相關研究整理為三個方向：

1. **領域內時間序列異常偵測（In-domain TSAD）：** 包含統計方法、距離方法，以及預測或重建誤差方法；通常需要領域資料，泛化能力可能受限。
2. **基礎模型與 LLM：** 嘗試使用預訓練時間序列編碼器或直接提示 LLM，但長距離上下文理解與 Token 成本仍是挑戰。
3. **視覺與 VLM 異常偵測：** 將時間序列繪製成圖表交由 VLM 判斷；若只使用小型滾動視窗，可能難以捕捉長距離上下文。

## 4. 解決方案

本研究提出 Zero-shot 兩階段框架，將異常偵測拆成定位（Localization）與驗證（Verification）。

### 4.1 ViT4TS：視覺篩選

1. 將一維時間序列轉換成二維折線圖影像。
2. 使用 rolling windows 建立多張視窗影像。
3. 透過預訓練視覺模型擷取 patch-level 特徵。
4. 使用 multi-scale embedding 與 cross-patch comparison 比較不同視窗的局部視覺特徵。
5. 建立 anomaly map，計算異常分數並產生候選異常區間。

### 4.2 VLM4TS：異常驗證與修正

將完整時間序列圖與候選異常區間提供給 VLM，透過提示要求模型：
- 保留經確認的異常區間。
- 移除被判定為誤報的區間。
- 補充可能被第一階段遺漏的異常區間。
- 提供信心分數及簡短文字解釋。

## 5. 實驗設計

### 5.1 資料集與比較方法

原始心得記錄研究使用 11 個 benchmark datasets，涵蓋天文感測器及網路流量等資料。比較方法包括統計方法、深度學習模型、時間序列基礎模型、LLM 方法及 VLM 基準方法。

### 5.2 評估方式

研究使用連續異常分數與平滑處理，並依閾值判定異常。原始心得亦整理了整體偵測表現、不同任務類型的表現、消融實驗，以及不同視覺骨幹模型的效率比較。

### 5.3 實驗觀察

依原始心得整理：
- VLM4TS 在 11 個資料集中的 9 個取得最佳表現。
- 在重視上下文異常的真實世界資料集上表現較佳。
- 異常密度高的資料集可能較具挑戰，因為方法對異常稀少的假設可能影響判斷。
- 消融實驗用於檢驗 patch-level embedding、cross-patch matching、多尺度特徵及視覺篩選階段的貢獻。

> **資料核對提醒：** 本頁內容由既有閱讀心得轉寫。正式公開前，建議再對照論文原文確認資料集數量、評估設定、實驗數值及模型名稱。

## 6. 結論

本研究透過兩階段架構結合視覺模型的候選異常定位能力與 VLM 的上下文理解能力，嘗試改善直接使用 VLM 判讀時間序列時的定位與效率問題。

第一階段 ViT4TS 負責產生候選區間，第二階段 VLM4TS 再進行驗證與修正。這種將任務拆分為定位與驗證的設計，是本研究的重要特色。

從閱讀角度來看，值得進一步理解的是：視覺特徵比較如何保留時間序列的局部變化，以及 VLM 在不同異常密度與不同領域資料上的泛化能力。

## References

- [論文連結](https://doi.org/10.48550/arXiv.2506.06836)
- [官方程式碼](https://github.com/ZLHe0/VLM4TS)
