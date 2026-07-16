# 破裂腹部大動脈瘤：術前壁応力予測の後ろ向き検証（匿名化症例研究）

Retrospective validation of pre-rupture wall-stress prediction against the actual
rupture site in a ruptured infrarenal abdominal aortic aneurysm (AAA) — a single,
fully de-identified case study.

## 概要
同一患者の腎下部AAAについて、**破裂の約9.5か月前**の待機CTから血流(CFD)と壁応力(FEA)を
計算し、**実際の破裂部位**（後壁・左・分岐部から約5cm頭側）および術後経過と照合した。

- 壁応力FEAの**高応力部位が実破裂部位と一致**。
- 破裂前 → 破裂 → 術後の3時点で瘤の増大・破裂・修復を3D可視化。
- 血流CFDで瘤中央は低WSS＋高OSI（血栓形成環境）。

**→ レポート本体は [`index.html`](index.html)（GitHub Pages で閲覧可）。**

## 方法
- セグメンテーション：TotalSegmentator
- 壁応力：中空壁シェル（marching cubes → meshpy/tetgen hole）＋ scikit-fem 線形弾性
  （E=2 MPa, ν=0.45, 内圧 16 kPa）
- CFD：OpenFOAM (pimpleFoam)、823,279セル、腎下部三相性入口波形（平均1.2 L/min）、
  1心拍0.9秒（約67 bpm）、3心拍中の最終心拍 → TAWSS/OSI/RRT

## 限界
壁厚一様・ILT未考慮・線形弾性・壁厚方向1要素、境界条件による変位アーティファクト、
汎用入口波形。単一例・仮説生成的。

## 倫理・匿名化
札幌医科大学の施設方針に基づき、本症例報告は**臨床倫理委員会の承認を必要としない**。
患者本人から臨床情報・CT画像・術中写真の掲載同意を得ている。公開データは
**匿名化済み**（氏名・患者ID・撮影日等の識別情報を削除、日付は相対表記）。
図中の内部コード名は患者を特定しない。

## 構成
```
index.html         レポート本体
assets/            図・動画（匿名名）
.nojekyll          GitHub Pages 設定
```
