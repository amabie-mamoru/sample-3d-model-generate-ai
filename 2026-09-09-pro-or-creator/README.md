# 3Dモデル生成AI をいろいろ試してみた (Pro / Creator プラン編)

## 記述日

2026/09/09

※生成AIは進化が激しい分野のため明記
※ちょうど Tripo 3D に Multi-views input が可能になったタイミング

## 比較AI

有料プラン(Pro/Creatorなど)での検証。現時点では Tripo AI のみ画像を配置済み。Rodin / Meshy は追って追加予定

- Tripo AI
- Rodin (追加予定)
- Meshy (追加予定)

## サンプル画像

### 建築物

<img src="./images/sample-building.png">

#### 採択の理由

* カジュアルゲームで育成要素として要求されがち
* アシンメトリー
* 構造が複雑でフロントビューからバックビューがしづらい

#### 余談

ChatGPT Images 2.0 でも、今回の画像を生成するのに 15 試行した

### ヒューマロイド

<img src="./images/sample-humaroid.png">

#### 採択の理由

* なるべくシンプルかつカジュアルゲームのテイストに合わせたモデル
* クリーチャーは構造によって精度差が大きそうなので人

#### 余談

ChatGPT Images 2.0 で今回の画像を生成するのに 5 試行

### アイテム

<img src="./images/sample-item.png">

#### 採択の理由

* シンメトリー
* 表から裏が想像がつきずらそうなアイテム

#### 余談

ChatGPT Images 2.0 で今回の画像を生成するのに 1 試行

## Tripo AI

### 前提

#### 生成手順

Multi views からモデルを生成する

<img src="./images/tripo-multi-views-manual-upload.png">

上記手順で3面図を **そのまま読み込ませず** 3つに分割した上で手動で向きに合わせてアップロードすることを推奨する（その方が圧倒的に精度が高かった）

right も準備できるなら理想だが、画像生成で 4 views で整合性を取った画像を用意しようとすると、その準備に多くの時間が取られるため、今回は3面図から生成させている

### Building

#### 4 views + oblique

Front|Left|Back|Right|Oblique1|Oblique2
---|---|---|---|---|---
<img src="./images/tripo-building-wireframe-front.png">|<img src="./images/tripo-building-wireframe-left.png">|<img src="./images/tripo-building-wireframe-back.png">|<img src="./images/tripo-building-wireframe-right.png">|<img src="./images/tripo-building-wireframe-oblique1.png">|<img src="./images/tripo-building-wireframe-oblique2.png">
<img src="./images/tripo-building-texture-front.png">|<img src="./images/tripo-building-texture-left.png">|<img src="./images/tripo-building-texture-back.png">|<img src="./images/tripo-building-texture-right.png">|<img src="./images/tripo-building-texture-oblique1.png">|<img src="./images/tripo-building-texture-oblique2.png">

#### その他（ズームして見た場合）

<img src="./images/tripo-building-zoomup-window.png">
<img src="./images/tripo-building-zoomup-back.png">
<img src="./images/tripo-building-zoomup-top.png">

### Humanoid

#### 4 views + oblique

Front|Left|Back|Right|Oblique1|Oblique2
---|---|---|---|---|---
<img src="./images/tripo-humaroid-wireframe-front.png">|<img src="./images/tripo-humaroid-wireframe-left.png">|<img src="./images/tripo-humaroid-wireframe-back.png">|<img src="./images/tripo-humaroid-wireframe-right.png">|<img src="./images/tripo-humaroid-wireframe-oblique1.png">|<img src="./images/tripo-humaroid-wireframe-oblique2.png">
<img src="./images/tripo-humaroid-texture-front.png">|<img src="./images/tripo-humaroid-texture-left.png">|<img src="./images/tripo-humaroid-texture-back.png">|<img src="./images/tripo-humaroid-texture-right.png">|<img src="./images/tripo-humaroid-texture-oblique1.png">|<img src="./images/tripo-humaroid-texture-oblique2.png">

#### その他（ズームして見た場合）

<img src="./images/tripo-humaroid-zoomup-bag.png">
<img src="./images/tripo-humaroid-zoomup-eyes.png">
<img src="./images/tripo-humaroid-zoomup-ribbon.png">

### Item

#### 4 views + oblique

Front|Left|Back|Right|Oblique1|Oblique2
---|---|---|---|---|---
<img src="./images/tripo-item-wireframe-front.png">|<img src="./images/tripo-item-wireframe-left.png">|<img src="./images/tripo-item-wireframe-back.png">|<img src="./images/tripo-item-wireframe-right.png">|<img src="./images/tripo-item-wireframe-oblique1.png">|<img src="./images/tripo-item-wireframe-oblique2.png">
<img src="./images/tripo-item-texture-front.png">|<img src="./images/tripo-item-texture-left.png">|<img src="./images/tripo-item-texture-back.png">|<img src="./images/tripo-item-texture-right.png">|<img src="./images/tripo-item-texture-oblique1.png">|<img src="./images/tripo-item-texture-oblique2.png">

#### その他（ズームして見た場合）

<img src="./images/tripo-item-zoomup-back-string.png">
<img src="./images/tripo-item-zoomup-bell-string.png">
<img src="./images/tripo-item-zoomup-texture.png">

## Rodin AI

### 前提

#### 生成手順

Image to 3D で三面図をアップロードし、アップロードした画像右上部に表示されるオプションから Crop を選択して、三面図を3つの画像に分ける。このとき、何を表現している画像かを Direction から選択もできる

その後、必要に応じて Private にした上で、AI モデル Gen-2.5 の Extreme-High（時間がかかるが高品質）が現状 x1 コストなのでこれで生成する

### Building

### Humaroid

### Item

## Meshy AI

(追加予定)

### 前提

#### 生成手順

### Building

#### Wireframe

説明|見た目
---|---

#### Texture

説明|見た目
---|---

#### その他

### Humaroid

#### Wireframe

説明|見た目
---|---

#### Texture

説明|見た目
---|---

#### その他

### Item

#### Wireframe

説明|見た目
---|---

#### Texture

説明|見た目
---|---

#### その他
