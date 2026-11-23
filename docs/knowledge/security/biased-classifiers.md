---
title: "Biased Classifiers（偏差分類器）"
category: "Intrusion Detection"
tags: ["False Positive", "False Negative", "Anomaly Detection"]
---

# Biased Classifiers（偏差分類器）

## 1. 基本概念

在 Meta-IDS 論文的架構中，Biased Classifiers 指額外設計的分類器，用來針對 Mean Shift 分群可能產生的誤報（False Positive）與漏報（False Negative）進行補充判斷。此處說明的是該論文中的特定設計，不代表所有文獻中的同名用語都採用相同架構。

## 2. 核心原理

依原心得描述，系統使用兩個以隨機森林為基礎的分類器，分別處理被錯誤判斷為正常的攻擊資料，以及被錯誤判斷為攻擊的正常資料。當分群結果信心程度不足時，系統將可疑資料交由偏差分類器進一步判斷。

## 3. 主要特色

- 與 Mean Shift 分群結果搭配使用。
- 分別針對漏報與誤報進行修正。
- 依原心得描述，兩個分類器皆以隨機森林為基礎。

## 4. 應用情境

在 Meta-IDS 中，偏差分類器用於補強未知零日攻擊偵測，降低單獨使用 Mean Shift 時的錯誤判斷。

## 5. 優點與限制

**優點：** 可針對分群模型的特定錯誤類型增加第二階段判斷，改善未知攻擊偵測結果。

**限制：** 額外分類器會增加系統複雜度；其成效依賴分群輸出、訓練資料及錯誤樣本處理方式。這裡的描述依據單篇論文心得，不宜直接泛化為通用標準方法。

## 6. 相關論文

- [Meta-IDS: Meta-Learning-Based Smart Intrusion Detection System for IoMT Network](../../papers/meta-ids-iomt-intrusion-detection.md)

## 7. 相關知識

- [Mean Shift Clustering（平均飄移分群）](mean-shift-clustering.md)
