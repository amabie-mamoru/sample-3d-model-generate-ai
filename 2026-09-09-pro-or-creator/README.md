# 3Dモデル生成AI をいろいろ試してみた (Pro / Creator プラン編)

## 記述日

2026/09/09

※生成AIは進化が激しい分野のため明記
※ちょうど Tripo 3D に Multi-views input が可能になったタイミング

## 比較AI

有料プラン(Pro/Creatorなど)での検証

- Tripo 3D
- Rodin 3D

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

## Tripo 3D

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

* Topology: Quad
* Faces: 5,055
* Vertices: 5,867

#### その他（ズームして見た場合）

<img src="./images/tripo-building-zoomup-window.png">

補間された側の窓が上窓・下窓共にかけている

<img src="./images/tripo-building-zoomup-back.png">

背面の草がメッシュから破綻

<img src="./images/tripo-building-zoomup-top.png">

屋根のポリゴンが欠けている

### Humanoid

#### 4 views + oblique

Front|Left|Back|Right|Oblique1|Oblique2
---|---|---|---|---|---
<img src="./images/tripo-humaroid-wireframe-front.png">|<img src="./images/tripo-humaroid-wireframe-left.png">|<img src="./images/tripo-humaroid-wireframe-back.png">|<img src="./images/tripo-humaroid-wireframe-right.png">|<img src="./images/tripo-humaroid-wireframe-oblique1.png">|<img src="./images/tripo-humaroid-wireframe-oblique2.png">
<img src="./images/tripo-humaroid-texture-front.png">|<img src="./images/tripo-humaroid-texture-left.png">|<img src="./images/tripo-humaroid-texture-back.png">|<img src="./images/tripo-humaroid-texture-right.png">|<img src="./images/tripo-humaroid-texture-oblique1.png">|<img src="./images/tripo-humaroid-texture-oblique2.png">

* Topology: Quad
* Faces: 6,261
* Vertices: 5,755

#### その他（ズームして見た場合）

<img src="./images/tripo-humaroid-zoomup-bag.png">

バッグの模様が破綻している

<img src="./images/tripo-humaroid-zoomup-eyes.png">

目・眉毛・髪・口などテクスチャが崩れている

<img src="./images/tripo-humaroid-zoomup-ribbon.png">

リボン・帽子もデクスチャが崩れている

### Item

#### 4 views + oblique

Front|Left|Back|Right|Oblique1|Oblique2
---|---|---|---|---|---
<img src="./images/tripo-item-wireframe-front.png">|<img src="./images/tripo-item-wireframe-left.png">|<img src="./images/tripo-item-wireframe-back.png">|<img src="./images/tripo-item-wireframe-right.png">|<img src="./images/tripo-item-wireframe-oblique1.png">|<img src="./images/tripo-item-wireframe-oblique2.png">
<img src="./images/tripo-item-texture-front.png">|<img src="./images/tripo-item-texture-left.png">|<img src="./images/tripo-item-texture-back.png">|<img src="./images/tripo-item-texture-right.png">|<img src="./images/tripo-item-texture-oblique1.png">|<img src="./images/tripo-item-texture-oblique2.png">

* Topology: Quad
* Faces: 5,626
* Vertices: 5,287

#### その他（ズームして見た場合）

<img src="./images/tripo-item-zoomup-back-string.png">

紐が仮面にくっつく形で表現されてしまっている

リメッシュを試していないので改善の余地あり

<img src="./images/tripo-item-zoomup-bell-string.png">

鈴を紐が貫通している

<img src="./images/tripo-item-zoomup-texture.png">

表面の模様も滲んでいる

## Rodin 3D

### 前提

#### 生成手順

Image to 3D で三面図をアップロードし、アップロードした画像右上部に表示されるオプションから Crop を選択して、3面図を3つの画像に分ける。このとき、何を表現している画像かを Direction から選択する

<img src="./images/rodin-setup-direction1.png">
<img src="./images/rodin-setup-direction2.png">

その後、必要に応じて Private にした上で、AI モデル Gen-2.5 の Extreme-High（時間がかかるが高品質）が現状 x1 コストなのでこれで生成する

生成されると以下ダイアログが表示される

<img src="./images/rodin-humaroid-setup-model.png">

四辺形メッシュで法線ベイクオプションを有効の上、最大メッシュでモデルを確認する

<img src="./images/rodin-humaroid-setup-mirror.png">

モデルによっては対照かどうかを聞かれる。聞かれない場合もあり、判定は Rodin まかせ。今回は Humaroid は非対称、Item は対称で生成している

<img src="./images/rodin-humaroid-setup-texture.png">

テクスチャの生成モデルは High を指定している。 Extreme High にすればより改善する可能性あり。ディティールはデフォルトの 7 を指定

<img src="./images/rodin-humaroid-setup-export.png">

出力オプションは High-poly, 4K がよかったが、プラン的にできなかったので 2K で出力している

以降に示す確認は Blender で行っている

なぜなら、 Rodin 3D のプレビューが軸を使った真正面などの表現ができず、ズームにも制限があったりでモデルを直接みないと確認できない点が多かったためである

### Building

#### 4 views + oblique

Front|Left|Back|Right|Oblique1|Oblique2
---|---|---|---|---|---
<img src="./images/rodin-building-wireframe-front.png">|<img src="./images/rodin-building-wireframe-left.png">|<img src="./images/rodin-building-wireframe-back.png">|<img src="./images/rodin-building-wireframe-right.png">|<img src="./images/rodin-building-wireframe-oblique1.png">|<img src="./images/rodin-building-wireframe-oblique2.png">
<img src="./images/rodin-building-texture-front.png">|<img src="./images/rodin-building-texture-left.png">|<img src="./images/rodin-building-texture-back.png">|<img src="./images/rodin-building-texture-right.png">|<img src="./images/rodin-building-texture-oblique1.png">|<img src="./images/rodin-building-texture-oblique2.png">

* Topology: Quad
* Faces: 46,076
* Vertices: 61,071

#### その他（ズームして見た場合）

<img src="./images/rodin-building-zoomup-door.png">

そもそもメッシュが波打っている。Rodin はモデル確認時にメッシュの状態やワイヤーフレームでの確認をすることが 2026/09/09 現在できない

メッシュの状態確認は目視でしか行えず、モデル確認ボタンを押下後（モデル生成後）しか確認できず、ワイヤーフレームでの確認もモデル生成後にしか確認できない。また、モデルの再生成はモデル生成後行うことができず、Creditを利用して新規に生成するしかない

<img src="./images/rodin-building-zoomup-grass.png">

背面の草木も壁と一体化している

<img src="./images/rodin-building-zoomup-sign.png">

特に補間された右側は草が屋根と同化したり、家と表札が同化してしまっている

### Humaroid

#### 4 views + oblique

Front|Left|Back|Right|Oblique1|Oblique2
---|---|---|---|---|---
<img src="./images/rodin-humaroid-wireframe-front.png">|<img src="./images/rodin-humaroid-wireframe-left.png">|<img src="./images/rodin-humaroid-wireframe-back.png">|<img src="./images/rodin-humaroid-wireframe-right.png">|<img src="./images/rodin-humaroid-wireframe-oblique1.png">|<img src="./images/rodin-humaroid-wireframe-oblique2.png">
<img src="./images/rodin-humaroid-texture-front.png">|<img src="./images/rodin-humaroid-texture-left.png">|<img src="./images/rodin-humaroid-texture-back.png">|<img src="./images/rodin-humaroid-texture-right.png">|<img src="./images/rodin-humaroid-texture-oblique1.png">|<img src="./images/rodin-humaroid-texture-oblique2.png">

* Topology: Quad
* Faces: 46,380
* Vertices: 55,640

#### その他（ズームして見た場合）

<img src="./images/rodin-humaroid-zoomup-bag.png">

カバンのテクスチャに歪み

<img src="./images/rodin-humaroid-zoomup-cloth.png">

服のメッシュが対称性がなく、スカルプトを適応したようなメッシュ形状

<img src="./images/rodin-humaroid-zoomup-face-mesh.png">

顔のメッシュ（特に目）も対称指定を入れなかったせいか、左右で表現が違う

<img src="./images/rodin-humaroid-zoomup-face-texture.png">

髪が肌と一体化しているメッシュに加えて、耳が二重に生成される

斜めからの View も生成時に渡せば改善されるかもしれない(が、ここにコストをかけすぎると、AI で生成する価値が下がる)

<img src="./images/rodin-humaroid-zoomup-hand.png">

手がひとまとまりのメッシュ

### Item

#### 4 views + oblique

Front|Left|Back|Right|Oblique1|Oblique2
---|---|---|---|---|---
<img src="./images/rodin-item-wireframe-front.png">|<img src="./images/rodin-item-wireframe-left.png">|<img src="./images/rodin-item-wireframe-back.png">|<img src="./images/rodin-item-wireframe-right.png">|<img src="./images/rodin-item-wireframe-oblique1.png">|<img src="./images/rodin-item-wireframe-oblique2.png">
<img src="./images/rodin-item-texture-front.png">|<img src="./images/rodin-item-texture-left.png">|<img src="./images/rodin-item-texture-back.png">|<img src="./images/rodin-item-texture-right.png">|<img src="./images/rodin-item-texture-oblique1.png">|<img src="./images/rodin-item-texture-oblique2.png">

* Topology: Quad
* Faces: 46,802
* Vertices: 52,259

#### その他（ズームして見た場合）

<img src="./images/rodin-item-zoomup-back-string.png">

後ろの紐が三重になっている。リモデルで改善の余地あり

<img src="./images/rodin-item-zoomup-bell1.png">

紐と鈴が繋がっていない

<img src="./images/rodin-item-zoomup-bell2.png">

光源を正面に指定しているのに、光の映り方が異なり、そもそもマテリアルの質感が違う
