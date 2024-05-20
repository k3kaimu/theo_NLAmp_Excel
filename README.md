# 非線形増幅器と非線形キャンセラの理論解析エクセルシート

このExcelファイルでは，非線形自己干渉キャンセラの自己干渉除去性能を理論解析します．

## 信号モデル

送信信号 $x$ を平均 $0$ ，分散 $1$ の複素ガウス分布 $\mathcal{CN}(0, 1)$ に従う信号とします．
この信号を，電力増幅器に入力して，以下の受信信号 $y$ を得るとします．
ただし， $f(x)$ は増幅器の伝達関数です．

$$
y = f(x)
$$

この受信自己干渉信号に対して，次の非線形自己干渉キャンセラを考えます．

$$
c(x) = \sum_{p=1,3,\cdots}^{N_c} c_p x|x|^{p-1}
$$

ここで， $c_p$ は以下の残留自己干渉電力 $I^\mathrm{R}$ が最小になるように推定されるとします．

$$
I^\mathrm{R} = \mathbb{E}\left[\left| f(x) - c(x) \right|^2\right]
$$

このときの非線形自己干渉キャンセラの除去性能を解析します．

## 使い方

1. B列に増幅器の伝達関数である $f(x)$ を入力してください．初期値は $s=1$ のRappモデルになっています．
2. D9からG9までが各次数の非線形キャンセラの除去量です．

## 詳細

このページにおけるSICR （Self-Interference Cancellation Ratio）特性は出力の線形成分と非線形成分の電力比であり，次のように定義されます．

$$
\mathrm{SICR}\text{ (dB)} = 10 \log_{10} \frac{I}{I^\mathrm{R}} = 10 \log_{10} \frac{P_1 + P_3 + P_5 + \cdots}{P_{N_c+2} + P_{N_c+4} + P_{N_c+6} + \cdots} = 10 \log_{10} \frac{P_\mathrm{tot}}{P_\mathrm{tot} - P_1 - P_3 - \cdots - P_{c}}
$$

ただし， $P_1$ ,  $P_3$ ,  $P_5$ , ...はそれぞれ線形成分と3次，5次の歪み成分の電力を表しています．
また， $P_\mathrm{tot}$ は全自己干渉電力で， $N_c$ は非線形キャンセラの最大次数です．
$P_n$ は増幅器の伝達関数 $f(x)$ に対して次のように計算できます．

$$
P_n = \left| \mathbb{E}\left[ \psi_n^{*}(x) f(x) \right] \right|^2
$$

$$
P_\mathrm{tot} = \mathbb{E}\left[ \left| f(x) \right|^2 \right]
$$

ここで，  $\psi_n(x)$ は以下のように定義されます．

$$
\psi_{2m+1}(x) = \frac{1}{\sqrt{m+1}} L_m^1(|x|^2) x
$$

これらの詳細については以下の論文を参照してください．
* K. Komatsu, Y. Miyaji and H. Uehara, "Theoretical Analysis of In-Band Full-Duplex Radios With Parallel Hammerstein Self-Interference Cancellers," in IEEE Transactions on Wireless Communications, vol. 20, no. 10, pp. 6772-6786, Oct. 2021, doi: 10.1109/TWC.2021.3076496.</li>
* K. Komatsu, Y. Miyaji, H. Uehara and T. Matsumura, "Theoretical Investigation and Optimization of Power Amplifier Nonlinearity for In-Band Full-Duplex Radios," in IEEE Transactions on Wireless Communications, vol. 22, no. 5, pp. 3384-3396, May 2023, doi: 10.1109/TWC.2022.3217765.</li>
