<script type="text/x-mathjax-config">MathJax.Hub.Config({tex2jax:{inlineMath:[['$','$'],['\\(','\\)']],processEscapes:true},CommonHTML: {matchFontHeight:false}});</script>
<script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML"></script>

[ホーム](../index.md) / [エクスパンダーグラフ](expander-graph.md)
# エクスパンダーグラフ

エクスパンダーグラフとは, ランダムウォークの混交が非常に早いという強力な性質を持つグラフの総称で,
誤り訂正符号や計算量理論などの擬似ランダムネスの文脈で幅広く応用されています.

{: .box-def}
**定義 (エクスパンダーグラフ).**
頂点数$n$のグラフ$G=(V,E)$ に対し, その<a href="/2024-11-20-graph/#正規化された隣接行列">正規化された隣接行列</a>
$P\in[0,1]^{V\times V}$ の固有値 $1=\lambda_1\ge \lambda_2\ge \dots \ge \lambda_n \ge -1$ に対して
$$
\lambda(P):=\max\{|\lambda_2|,|\lambda_n|\}
$$
とする. パラメータ $\lambda\in[0,1]$ に対し, $\lambda(P) \le \lambda$ を満たすグラフを <span style="color: tomato;">**$\lambda$-エクスパンダー ($\lambda$-expander)**</span> という.

> **注釈.**
> 無向グラフの隣接行列が対称行列となることから, 正規化された隣接行列も常に実固有値を持つことが示せます. 有向グラフでは必ずしも実固有値性は成り立ちません.
> 任意のグラフの正規化された隣接行列$P$は各行の行和が$1$に等しいため, 全成分$1$のベクトル $\mathbf{1}$に対して$P \mathbf{1} = \mathbf{1}$を満たします. このことから必ず$1$を固有値として持ちます. 実は固有値$1$が最大固有値となるため, 常に$\lambda_1=1$が成り立ちます.

上記の定義では自明な第一固有値$\lambda_1=1$以外の固有値が絶対値の意味で小さいことを要請していますが, 第二固有値が小さいという性質のみを満たすグラフを片側エクスパンダーといいます.

{: .box-def}
**定義 (片側エクスパンダーグラフ).**
頂点数$n$のグラフ$G=(V,E)$ の<a href="/2024-11-20-graph/#正規化された隣接行列">正規化された隣接行列</a>
$P\in[0,1]^{V\times V}$ の固有値 $1=\lambda_1\ge \lambda_2\ge \dots \ge \lambda_n \ge -1$ に対して, $|\lambda_2| \le \lambda$を満たすグラフを <span style="color: tomato;">**片側$\lambda$-エクスパンダー ($\lambda$-expander)**</span> という.

一般に$\lambda$が小さいほど高いエクスパンダー性を持つとみなします. 

# エクスパンダーグラフの例
### 完全グラフ
$n$頂点の完全グラフの正規化された隣接行列$P$は, 単に行列$I$と全成分$1$の行列$J$を用いて, $P=\frac{1}{n-1}(J-I)$と表せます. 第一ベクトルは $\mathbf{1}$ であり, 他の固有ベクトル$x$は全て$\mathbf{1}$に直交するため$J \mathbf{1} = 0$です. 従って$Px = -\frac{1}{n-1}x$となるため, 第一以外の固有値は全て$-\frac{1}{n-1}$なので, 完全グラフ$K_n$は$\frac{1}{n-1}$-エクスパンダーです.

### 閉路グラフ
頂点数$n$の閉路グラフとは, 頂点集合$$V=\{ 0,\dots,n-1 \}$$
に対して辺集合
が $$E= \{\{v0,v1\},\dots,\{v_{n−2},v_{n-1}\},\{v_{n-1},v_0\}\}$$ で与えられるグラフ$(V,E)$である. 頂点数$n$が偶数のとき, 閉路グラフは二部グラフとなります.
ここでは$\omega = \exp(2\pi i/n)$を$1$の冪根とし, 頂点集合を
$$V = \{\omega^i \colon i=0,\dots,n-1\}$$
と同一視し,各辺を$$\{\omega^i,\omega^{i+1}\}$$ で表します.
任意の関数$f \colon V \to \mathbb{R}$に正規化された隣接行列$P$を左から作用させると

$$
Pf(\omega^i) = \frac{f(\omega^{i-1}) + f(\omega^{i+1})}{2}
$$

を得ます. そこで, 各
$$k\in \{0,\dots,n-1\}$$
に対して関数
$x_k \colon \omega^j \mapsto \omega^{kj}$
を考えると,
$P x_k (\omega^j) = \frac{ \omega^{k(j-1)} + \omega^{k(j+1)} }{2} = \frac{\omega^{-k}+\omega^k}{2}\cdot x_k(\omega^j)$を得ます.
従って各$k= 0,\dots,n−1$に対し, $x_k$はそれぞれ固有値 $\frac{\omega^k + \omega^{-k}}{2} = \cos \frac{2\pi k}{n}$に対応する固有ベクトルとなります.

これらの固有値を降順に並べて$\lambda_1 \ge \dots \ge \lambda_n$とすると,
$\lambda_2 = \cos \frac{2\pi}{n} = 1-\frac{4\pi^2}{2n^2} + O(n^{-4})$です. 頂点数$n$が偶数のときは$\lambda_n =−1$, 頂点数$n$が奇数のときは
$\lambda_n = \cos\pi\left(1-\frac{1}{n}\right) = -1+\frac{\pi^2}{2n^2} - O(n^{-4})$ ですので, 頂点数$n$が奇数のときの閉路グラフは$\cos \frac{π}{n}$-エクスパンダーであり, $n\to\infty$の漸近を考えると$\lambda(P)=1-\Theta(n^{-2})$となります.





