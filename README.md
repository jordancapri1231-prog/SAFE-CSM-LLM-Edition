# SAFE-CSM — LLM Edition
SAFE-CSM (LLM Edition) is a SAFE-layer external observation framework designed to stabilize contextual drift in Large Language Model outputs.  
This repository contains the public demonstration code, figures, and documentation for the LLM-focused version of SAFE-CSM.

---

# English

## Overview
SAFE-CSM (LLM Edition) provides:
- External observation of Δφ drift in LLM contextual output  
- Lightweight stability feedback without modifying or training the model  
- Evaluation tools for comparing “LLM only” vs “LLM + SAFE-CSM”  
- Fully transparent and SAFE-compliant implementation  

This edition does not include reinforcement loops, adaptive control, psychological models, or internal inspection.  
All analysis is limited to externally observable output signals.

## Contents
- `SAFE-CSM_LLM_demo.py`  
- `SAFE-CSM_LLM_demo.txt`  
- `SAFE-CSM_LLM_Report.txt`  
- `SAFE-CSM_LLM_FullDescription.txt`  
- `LICENSE_SAFE.txt`  
- Figures  
  - `figure_1_fixed_to_release.png`  
  - `figure_2_sink_control.png`  
  - `figure_3_diverggence_stabilized.png`  

## Related Projects
- SAFE-CSM (Industry Edition)  
- CSM SAFE Core (Initial Evaluation Edition)

## Citation (OSF DOI)
Please cite the OSF DOI for reproduction and academic use:  
**[10.17605/OSF.IO/VAURE]**

## Contact
Research inquiries: **jordan.capri.1231@gmail.com**

---

# 日本語 / Japanese

## 概要
SAFE-CSM（LLM版）は、LLMの文脈出力における  
「ドリフト・固定化・過同期（オーバーシンク）」を  
外部から観測し、SAFEバンドへ戻すための  
**SAFE層・非適応型の観測フレームワーク** です。

モデル内部には一切アクセスせず、  
学習・最適化・強化なども行いません。

## 含まれるファイル
- `SAFE-CSM_LLM_demo.py`（実行可能デモ）  
- `SAFE-CSM_LLM_demo.txt`（説明）  
- `SAFE-CSM_LLM_Report.txt`（SAFEレポート）  
- `SAFE-CSM_LLM_FullDescription.txt`（拡張説明）  
- `LICENSE_SAFE.txt`（ライセンス）  
- 図（3種）  
  - `figure_1_fixed_to_release.png`  
  - `figure_2_sink_control.png`  
  - `figure_3_diverggence_stabilized.png`  

## 関連プロジェクト
- SAFE-CSM（産業版）  
- CSM SAFEコア（初期評価版）

## 引用（OSF DOI）
学術研究で使用する場合は、以下のDOIをご利用ください：  
**［10.17605/OSF.IO/VAURE］**

## 連絡先
研究・技術問い合わせ：  
**jordan.capri.1231@gmail.com**

