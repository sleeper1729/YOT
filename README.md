# Digital image inpainting based on markov random field
[Digital image inpainting based on markov random field](https://ieeexplore.ieee.org/document/1631558)の実装

## 論文の概要
この論文では、一部に欠損が生じた画像が与えられた時に、欠損部分を補完して元の画像を得るアルゴリズムを与えている。

欠損はマスク画像として与えられる。

画像の各ピクセルを頂点、隣り合ったピクセル同士には辺があると思って画像をグラフと見なし、対応するガウシアンマルコフ場を考える。

すると周辺化によって、画像の各ピクセルに対して、画素値の確率分布が得られる。欠損部分に対して、最大周辺事後確率推定を行うことで、欠損部分の補完を行う。

周辺事後確率分布は確立伝搬法によって計算する。

## 実装


## 実験方法

適当な画像とマスクを用意してアルゴリズムを適用するだけ。openCVの別アルゴリズムで補修した結果も用意してMSEを比較してみる。

### 元画像

![babel](https://github.com/sleeper1729/YOT/blob/main/inpainting/original.png)

こいつに下のように黒い円を描く。

### マスク画像

![masked](https://github.com/sleeper1729/YOT/blob/main/inpainting/masked.png)

この黒い部分を修復したい。

## 結果

論文の実装結果がこれ。元画像とのMSEは0.6918 (マスク部分だけだと80.95)。

![repaired](https://github.com/sleeper1729/YOT/blob/main/inpainting/repaired.png)

openCVのcv2.inpaintを使ったのがこれ。元画像とのMSEは0.7172 (マスク部分だけだと83.92)。

openCVのアルゴリズムは[Digital image inpainting based on markov random field](http://olivier-augereau.com/docs/2004JGraphToolsTelea.pdf)。

![opencv](https://github.com/sleeper1729/YOT/blob/main/inpainting/opencv.png)

## 備考

この例を見るに、左下のように、多少複雑な構造のある部分の修復は比較的難しそう。

[Fields of Experts: a framework for learning image priors](https://ieeexplore.ieee.org/document/1467533)には、学習を使ってもう少し周囲の構造を反映するように補修するアルゴリズムがのってるらしい。

また、ループのある場合の確率伝播法は必ずしも収束しないので、他の手段で分布を計算して比較したい。
