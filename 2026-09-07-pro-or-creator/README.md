# 3Dモデル生成AI をいろいろ試してみた (Pro / Creator プラン編)

## 記述日

2026/09/07

※生成AIは進化が激しい分野のため明記

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

ChatGPT Images 2.0 でも、今回の画像を生成するのに 14 試行した
あえてフロントビューは少し斜めにしている（2つ理由があり、一つは少し傾いていても正しく作れるかの検証。もう一つはこれを是正するのにさらに多大な試行が必要になる可能性があり、コスパが悪い）

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

Tripo AI は現在三面図に ***対応していない

そのため、三面図を読み込ませると3モデルが生成される

ここでの検証ポイントは Tripo は補完がすごいため、どういった補完がなされるかをベースにみてほしい

三面図から意図したモデルを作るのは現状 **できない**

#### 生成手順

生成時はきれいなトポロジーというオプションを指定して三面図画像を添付して生成している

### Building

#### Wireframe

説明|見た目
---|---
正面から見た場合|<img src="./images/tripo-building-wireframe-front.png">
背面から見た場合|<img src="./images/tripo-building-wireframe-back.png">
上斜めから見た場合|<img src="./images/tripo-building-wireframe-oblique.png">
下斜めから見た場合|<img src="./images/tripo-building-wireframe-oblique-reverse.png">

* side view の裏側（補完した部分）のメッシュが破綻
* front view の表側のメッシュが破綻（これは試行によって改善可能性あり）
* 床面のメッシュはない

#### Texture

説明|見た目
---|---
正面から見た場合|<img src="./images/tripo-building-texture-back.png">
背面から見た場合|<img src="./images/tripo-building-texture-front.png">
上斜めから見た場合|<img src="./images/tripo-building-texture-oblique.png">
下斜めから見た場合|<img src="./images/tripo-building-texture-oblique-reverse.png">

* テクスチャは全体的におおまかには正しいが、細部は色々おかしい

#### その他（ズームして見た場合）

<img src="./images/tripo-building-zoomup-oblique-good.png">

front view の右側はかなりいい感じで補完されている（意図通りかはおいといて）

<img src="./images/tripo-building-zoomup-oblique-reverse.png">

side view は陥没している

<img src="./images/tripo-building-zoomup-oblique.png">

front view のメッシュ破損

### Humanoid

#### Wireframe

説明|見た目
---|---
正面から見た場合|<img src="./images/tripo-humanoid-wireframe-front.png">
背面から見た場合|<img src="./images/tripo-humanoid-wireframe-back.png">
斜めから見た場合|<img src="./images/tripo-humanoid-wireframe-oblique.png">

* メッシュは基本補完されている部分も含めて綺麗め
* front view で補完された裏側のリュックは形状が違い、足は少し細い
* back view で補完された裏側の顔は形状が少し違い細め
* side view の奥側（補完されている側）が少しひしゃげている

#### Texture

説明|見た目
---|---
正面から見た場合|<img src="./images/tripo-humanoid-texture-front.png">
背面から見た場合|<img src="./images/tripo-humanoid-texture-back.png">
斜めから見た場合|<img src="./images/tripo-humanoid-texture-oblique.png">

* front view の帽子の部分がやや貫通している
* back view で補完された顔が補完できていない
* メッシュ同様に side view の奥側（補完されている側）がひしゃげている

#### その他

<img src="./images/tripo-humanoid-zoomup-back-back-face.png">

back view で補完された顔は輪郭が少しスリムで表情も補完できていない

<img src="./images/tripo-humanoid-zoomup-back-front-bag.png">

front view で補完されたカバンは三面図の意図通りではないが、ありえなくはない補完はなされている

テクスチャはやや崩れている

<img src="./images/tripo-humanoid-zoomup-oblique.png">

side view はメッシュもテクスチャも完全に崩れている

### Item

#### Wireframe

説明|見た目
---|---
正面から見た場合|<img src="./images/tripo-item-wireframe-back.png">
背面から見た場合|<img src="./images/tripo-item-wireframe-front.png">
斜めから見た場合|<img src="./images/tripo-item-wireframe-oblique.png">

* 表も裏も裏側の凹みも補完された部分も含めて front / back view は精度が高い
* side view は斜めから見ると少しわかるが奥側がひしゃげている

#### Texture

説明|見た目
---|---
正面から見た場合|<img src="./images/tripo-item-texture-back.png">
背面から見た場合|<img src="./images/tripo-item-texture-front.png">
斜めから見た場合|<img src="./images/tripo-item-texture-oblique.png">

* 三面図で描いた見えている側（補完していない側）はテクスチャの崩れはほぼない
* 補完した側はややズレがあるが許容範囲
* side view は奥側（補完されている側）がテクスチャも一部欠損がある

#### その他

<img src="./images/tripo-item-zoomup-back.png">

back view の裏側（保管された側）はかなり綺麗

<img src="./images/tripo-item-zoomup-oblique-reverse.png">

メッシュは表面もそうだが裏面からもひしゃげが見える

<img src="./images/tripo-item-zoomup-oblique.png">

ひしゃげがわかりやすいようにやや斜め下から見上げる形で見せたパターン

そもそも少し左（補完された側）に歪んでいる

## Rodin AI

### 前提

#### 生成手順

Image to 3D で三面図をアップロードし、アップロードした画像右上部に表示されるオプションから Crop を選択して、三面図を3つの画像に分ける。このとき、何を表現している画像かを Direction から選択もできる

その後、必要に応じて Private にした上で、AI モデル Gen-2.5 の Extreme-High（時間がかかるが高品質）が現状 x1 コストなのでこれで生成する

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
