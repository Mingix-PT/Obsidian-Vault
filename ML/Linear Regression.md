### Bài toán
Cho tập dữ liệu $\mathbf{X}$, cần tìm weight $\mathbf{w}$ và bias $b$ để dự đoán hàm tuyến tính $$\overset{\textasciicircum}{\mathbf{y}} =\mathbf{Xw}+b$$ 
### Hàm mất mát
Bình phương tối thiểu: $$l^{(i)}(\mathbf{w},b)=\frac{1}{2}(\overset{\textasciicircum}{y}^{(i)}-y^{(i)})^2$$
$$L(\mathbf{w},b)
=\frac{1}{n}\sum\limits^n_{i=1}l^{(i)}(\mathbf{w},b)
=\frac{1}{n}\sum\limits^n_{i=1}\frac{1}{2}(\mathbf{w^{T}x^{(i)}}+b-y^{(i)})^2
$$ 
### Nghiệm theo công thức
Nghiệm tối ưu toàn cục:
$$\mathbf{w^*},b^*=\underset{\mathbf{w},b}{argmin}\;L(\mathbf{w},b)$$
$$\mathbf{w^*}=\mathbf{(X^{T}X)^{-1}X^T}y$$
Tuy nhiên 