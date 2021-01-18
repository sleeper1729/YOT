# YOT
"Digital image inpainting based on markov random field" https://ieeexplore.ieee.org/document/1631558　の実装

## 論文の概要
この論文では、一部に欠損が生じた画像が与えられた時に、欠損部分を補完して元の画像を得るアルゴリズムを与えている。

欠損はマスク画像として与えられる。

画像の各ピクセルを頂点、隣り合ったピクセル同士には辺があると思って画像をグラフと見なし、対応するガウシアンマルコフ場を構成する。



