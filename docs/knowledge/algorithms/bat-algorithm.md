---
title: "Bat Algorithm（蝙蝠演算法）"
category: "Optimization Algorithm"
tags: ["Metaheuristic", "Hyperparameter Optimization"]
---

# Bat Algorithm（蝙蝠演算法）

## 1. 基本概念

Bat Algorithm 是一種受蝙蝠回聲定位行為啟發的群體式／仿生最佳化演算法，用於在候選解空間中搜尋較佳解。

## 2. 核心原理

演算法以候選解代表不同蝙蝠的位置，並透過速度、頻率、響度及脈衝發射率等概念控制搜尋與解的更新，使搜尋過程在探索新區域與利用已知較佳區域之間取得平衡。

## 3. 主要特色

- 屬於仿生式的啟發式最佳化方法。
- 透過群體中多個候選解進行搜尋。
- 可用於連續或經適當編碼的最佳化問題。

## 4. 應用情境

可用於參數搜尋及組合最佳化。Meta-IDS 使用 Bat Algorithm 搜尋弱學習器的超參數組合。

## 5. 優點與限制

**優點：** 不需要問題具備容易求導的目標函數，可用於複雜搜尋空間。

**限制：** 搜尋結果受參數設定與隨機性影響，無法保證找到全域最佳解；需與其他方法及基準比較。

## 6. 相關論文

- [Meta-IDS: Meta-Learning-Based Smart Intrusion Detection System for IoMT Network](../../papers/meta-ids-iomt-intrusion-detection.md)

## 7. 相關知識

- [BO-TPE](bo-tpe.md)
