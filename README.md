# YOT
"Digital image inpainting based on markov random field" https://ieeexplore.ieee.org/document/1631558　の実装

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

![babel](https://github.com/sleeper1729/YOT/blob/main/inpainting/original.jpg)
こいつに下のように黒い円を描く。

### マスク画像

![masked](https://github.com/sleeper1729/YOT/blob/main/inpainting/masked.jpg)
