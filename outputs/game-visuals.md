---
marp: true
theme: default
paginate: true
size: 16:9
style: |
  section { background: #111722; color: #f5f7fb; font-family: 'Yu Gothic', 'Noto Sans CJK JP', sans-serif; padding: 54px 70px; }
  h1 { color: #fff; font-size: 50px; letter-spacing: .02em; }
  h2 { color: #fff; font-size: 37px; margin-bottom: 18px; }
  p, li { font-size: 25px; line-height: 1.5; }
  strong { color: #a7d8ff; }
  section::after { color: #91a0b5; font-size: 14px; }
---

# ゲームの見た目をよくするあれこれ

3Dシーンの「Unityっぽさ」を減らすための調整

---

## 導入

![bg right:57%](assets/scene-before.png)

ゲームを作ってみたはいいものの見た目がしっくりこない
よく見るグラフィックになる

---

## マテリアル

BlenderのマテリアルのRoughnessの初期値は **0.5**。そのまま全素材へ使うと、表面の質感が似通いやすい。

素材ごとに反射の広がりを決める。金属、塗装、コンクリートを同じ値にしない。

![bg right:25% contain](assets/material.png)

---

## フォグ

遠い場所ほど霧を強めると、建物が空気になじみ、奥行きが出る。

**変更前**　　　　　　　　　　　　　　　 **変更後**

![width:520](assets/scene-before.png) ![width:520](assets/scene-fog.png)

---

## フォグの設定方法

![bg right:36% contain](assets/fog-settings.png)

Lighting → Environment → Other Settings の **Fog** をオンにする。

Fogの色、Mode、Densityをシーンに合わせて調整する。

---

## フォグと背景色

![bg right:38% contain](assets/camera-background-settings.png)

**Skyboxにはフォグが適用されない**ため、遠景と空の色が合わないことがある。

![width:520](assets/scene-aces-before.png)

Main Camera の Inspector で **Environment → Background Type** を **Solid Color** に変更する。

**Background** にフォグと近い色を設定し、空と遠景の境目を確認する。

---

## Bloom

明るい部分の周囲に光のにじみを作る。

**変更前**　　　　　　　　　　　　　　　 **変更後**

![width:520](assets/scene-fog.png) ![width:520](assets/scene-bloom.png)

**Threshold** は反応する明るさの境界、**Intensity** はにじみの強さ。

---

## Bloomの設定方法

![bg right:34% contain](assets/bloom-settings.png)

Hierarchyで **Global Volume** を選び、Inspectorの Bloom を開く。

![width:390](assets/global-volume-hierarchy.png)

Thresholdで街灯だけが主に反応するようにし、Intensityを調整する。

---

## Bloomが強すぎる例

**控えめ**　　　　　　　　　　　　　　　 **強すぎる例**

![width:520](assets/scene-bloom.png) ![width:520](assets/scene-bloom-over.png)

しきい値が低すぎると街全体が白くなる。光源以外もにじむ場合はThresholdを上げる。

---

## ACESの効果

HDRをSDRに変換するトーンマッピング。明るい部分と暗い部分の印象が変わる。

**Neutral**　　　　　　　　　　　　　　 **ACES**

![width:520](assets/scene-bloom.png) ![width:520](assets/scene-night-before.png)

---

## ACESの設定方法

![bg right:32% contain](assets/aces-settings.png)

Global Volume の **Tonemapping** を Neutral から ACES に変更する。

街灯と暗部の見え方を比較して確認する。

---

## 環境光を暗くした結果

ライトを消しても、Skybox由来の環境光は残る。

**変更前**　　　　　　　　　　　　　　　 **変更後**

![width:520](assets/scene-night-before.png) ![width:520](assets/scene-final.png)

建物と道路が暗くなり、街灯が目立つ。

---

## 環境光を暗くする設定方法

![bg right:35% contain](assets/environment-settings.png)

Lighting → Environment で **Environment Lighting** の Source を Color に変更し、Ambient Colorを暗くする。

---

## まとめ

![bg right:45%](assets/scene-final.png)

---

# 良きゲ制ライフを

~Thank you for listening~
