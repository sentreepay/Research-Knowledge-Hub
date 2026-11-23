---
title: "Meta-Learning（元學習）"
category: "Machine Learning"
tags: ["Ensemble Learning", "Model Generalization", "Learning to Learn"]
---

# Meta-Learning（元學習）

## 1. 基本概念

Meta-Learning 常被稱為「學習如何學習」，核心概念是利用多個任務或模型的經驗，學習更有效的學習方式或模型整合策略。不同研究中的元學習架構可能不同，需依具體方法判讀。

## 2. 核心原理

在本知識庫收錄的 Meta-IDS 論文中，元學習採用兩層式整合方式：第一層多個弱學習器各自對網路流量進行分類，第二層元學習器接收各弱學習器的預測結果，再學習如何整合這些結果並輸出最終分類。

## 3. 主要特色

- 可整合多個基礎模型的預測資訊。
- 元學習器負責學習模型輸出之間的組合方式。
- 可降低單一分類器對資料模式的依賴。
- 具體架構會隨研究目的而異。

## 4. 應用情境

可用於分類、跨任務快速適應及模型集成。在 Meta-IDS 中，XGBoost 擔任元學習器，整合六種弱學習器的預測結果，以辨識已知攻擊。

## 5. 優點與限制

**優點：** 能結合不同模型的判斷，利用模型間的互補資訊。

**限制：** 多層模型會增加訓練與維護成本；若基礎模型的錯誤高度相關，整合後也未必能改善結果。需避免將所有稱為 Meta-Learning 的方法都視為同一種架構。

## 6. 相關論文

- [Meta-IDS: Meta-Learning-Based Smart Intrusion Detection System for IoMT Network](../../papers/meta-ids-iomt-intrusion-detection.md)

## 7. 相關知識

- [XGBoost](xgboost.md)
