# 破裂腹部大動脈瘤：術前壁応力と破裂部位の後ろ向き比較

Retrospective comparison of pre-rupture wall stress with the subsequent rupture
site in an infrarenal abdominal aortic aneurysm — a de-identified case study.

## 概要

同一患者の腎下部AAAについて、破裂の約9.5か月前のCTAから壁応力FEAと血流CFDを実施し、その後の破裂関連部位および術後経過と後ろ向きに比較した。

- 真のposterior方向から最大主応力を再描画し、外表面p95 444.2 kPa、p99 718.6 kPaを再確認した。
- 左後壁には、後の破裂関連形態と近い頭尾方向レベルに局所的な応力上昇域がみられた。
- ただし全体最大値は前壁にあり、右posteriorの応力負荷は左posteriorより高かった。非剛体位置合わせも未実施であり、破裂部位を予測したとは結論しない。
- 破裂前、破裂時、術後の3時点を3D可視化した。
- OpenFOAMによるCFDは流体WSSの別解析で、破裂関連部位の比較には使用していない。

レポート本体は [`index.html`](index.html)（GitHub Pagesで閲覧可）。

## 方法

- セグメンテーション：TotalSegmentator
- FEA：scikit-fem、235,180四面体、公称壁厚1.8 mm、E=2 MPa、ν=0.45、内圧16 kPa、最大主応力
- CFD：OpenFOAM v2512 / pimpleFoam、823,279セル、腎下部三相性入口波形（平均1.2 L/min）、0.9秒周期（約67 bpm）、3周期中の最終周期を解析
- Figure 2：著者指定のposterior von Mises壁応力表示（別の腎動脈込み探索的モデル、0–430 kPa）。定性的可視化として使用

注意：採用したFigure 2Bの画像内タイトルは `maximum principal wall stress` ですが、保存された元スカラー場はvon Mises応力です。公開HTMLと原稿legendは元データに合わせて記載しています。投稿前に画像内タイトルを修正するか、最大主応力データから再描画してください。

## 限界

壁厚と材料特性を一様とした線形弾性モデル、ILT荷重伝達・局所壁強度の未評価、単一例、破裂までの形態変化、時点間の非剛体位置合わせと術野の空間登録が未実施。結果は仮説生成的な後ろ向き視覚比較であり、破裂位置の予測精度を示すものではない。

## 倫理・申告

札幌医科大学の施設方針に基づき、本症例報告は臨床倫理委員会の承認を必要としない。患者本人から臨床情報、CT画像、術中写真の掲載について書面同意を得た。公開データは匿名化済み。

- Funding：なし
- Competing interests：なし
- Acknowledgements：Not applicable
- OpenAI Codex：著者監督下でコード作成支援、数値照合、原稿・Figure整備に使用。全内容は著者が検証し責任を負う。

## 構成

```text
index.html         レポート本体
assets/            匿名化した図・動画
.nojekyll          GitHub Pages設定
```
