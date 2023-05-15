# Gaussian_process
ガウス過程と機械学習に関するコードです．

ガウス過程を使いたいときは参考程度にしてみてください．

# Gaussian_Process.ipynbについて
ガウス過程回帰を実装してみたファイルになります．

ブラウン運動もどきを生成し，実際にガウス過程回帰をしています．
## ガウス過程回帰の流れ
### カーネルの定義
まずはカーネルの定義です．このカーネルを持ったガウス過程を我々はモデル化します．
$$k(x , x^{'}) = \theta_1 \exp{\left( - \frac{(x - x^{'})^2}{\theta_2} \right)} + \theta_3 \delta(x , x^{'})$$
### 訓練データからカーネルを計算
モデル化したカーネルを使い，訓練データを用いてフィッティングします．
$$[K]_{ij} = \theta_1 \exp{\left( - \frac{(x_i - x_j)^2}{\theta_2} \right)} + \theta_3 \delta(x_i , x_j)$$
### 予測分布の計算
テストデータを用いて，各説明変数における目的変数の分布を計算します．
$$p(y^* | \vec{x}^* ,\mathcal{D}) = \mathcal{N} (\textbf{k}^{\top}_* K^{-1} \vec{y} , \textbf{k}_{**} - \textbf{k}^{\top}_* K^{-1} \textbf{k}_*)$$
### 予測分布の可視化
各点にガウス分布を定義できたら，それを可視化しました．可視化したのは期待値と標準偏差を2倍した範囲です．
## 実装したカーネル
### 教科書3.4と3.5のモデルをそのまま採用したコード
$$k(x , x^{\prime}) = \theta_1 \exp{\left( - \frac{(x - x^{\prime})^2}{\theta_2} \right)} + \theta_3 \delta(x , x^{\prime}) $$
とカーネルをモデル化しました．
### ランダムウォークの理論的な分散共分散行列を計算した上でのモデル化
$$k(x , x^{\prime}) = \theta_1 \exp{\left( - \frac{(x - x^{\prime})^2}{\theta_2} \right)} + \theta_3 \delta(x , x^{\prime}) + \theta_4 \min{\{x , x^{\prime}\}}$$
とカーネルをモデル化しました．
# Gaussian_Process_Chapter3.ipynbについて
教科書の図を再現したコードです．教科書のイメージがつかない方は参考にしてください．（だいぶ途中）
