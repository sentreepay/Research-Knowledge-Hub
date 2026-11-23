---
title: "SMOTE（合成少數類別過採樣技術）"
category: "Data Preprocessing"
tags: ["Class Imbalance", "Oversampling", "Machine Learning"]
---

# SMOTE（合成少數類別過採樣技術）

## 1. 基本概念

SMOTE（Synthetic Minority Over-sampling Technique）是一種處理類別不平衡的資料前處理方法，透過合成少數類別樣本，減少模型只偏向多數類別的情況。

## 2. 核心原理

SMOTE 通常會在少數類別樣本的特徵空間中尋找近鄰，並在樣本與近鄰之間插值，產生新的合成樣本，而不是單純複製既有資料。

## 3. 主要特色

- 以合成資料增加少數類別樣本數量。
- 常用於二元或多類別分類前處理。
- 可與多種分類器搭配。

## 4. 應用情境

適用於詐欺偵測、故障診斷及入侵偵測等少數類別較難蒐集的分類問題。Meta-IDS 使用 SMOTE 改善正常資料與攻擊資料之間的類別不平衡。

## 5. 優點與限制

**優點：** 可增加少數類別的訓練樣本，避免只依賴重複複製樣本。

**限制：** 若少數類別本身含有雜訊或類別邊界重疊，合成樣本可能加劇重疊；應只在訓練資料上執行，避免資料洩漏。

## 6. 相關論文

- [Meta-IDS: Meta-Learning-Based Smart Intrusion Detection System for IoMT Network](../../papers/meta-ids-iomt-intrusion-detection.md)

## 7. 相關知識

- [RFE（遞迴特徵消除）](rfe.md)
- [LDA（線性判別分析）](lda.md)
