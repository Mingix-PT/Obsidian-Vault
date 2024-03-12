### Bài toán
Cho tập dữ liệu $\mathbf{X}$, cần tìm weight $\mathbf{w}$ và bias $b$ để dự đoán hàm tuyến tính 
$$f(\mathbf{x})=w_0+w_1x_{1}+ w_2x_{2}+...+w_nx_n$$
$$\overset{\textasciicircum}{\mathbf{y}} =\mathbf{Xw}+b$$ 
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
Tuy nhiên không sử dụng vì tốn thời gian, tài nguyên tính toán

### Tối ưu bằng Gradient Descent
Sử dụng [Mini-batch Gradient Descent](Gradient%20Descent#Stochastic%20Gradient%20Descent) để tối ưu hàm mất mát:
![[Pasted image 20240311101517.png]]

![[Pasted image 20240311101537.png]]

B là số ví dụ mỗi mini batch, $\eta$ là tốc độ học

### Ridge regression
Thêm 1 hằng số phạt $\lambda$ vào công thức tối ưu $\mathbf{w}$
$$\mathbf{w}=\underset{\mathbf{w}}{argmin}\sum\limits^M_{i=1}(y_i-\mathbf{A_{i}w}^2)+\lambda\sum\limits^n_{j=0}\mathbf{w}_{j}^{2}$$
$\lambda$ là siêu tham số, không học mà phải điều chỉnh 1 cách thủ công tại mỗi vòng lặp
### Phân phối chuẩn 
Mật độ xác suất của phân phối chuẩn với kì vọng $\mu$ và phương sai $\sigma^2$: $$p(z)=\frac{1}{\sqrt{2\pi\sigma^2}}\exp(-\frac{1}{2\sigma^2}(z-\mu)^2)$$Giả định các quan sát bắt nguồn từ những quan sát nhiễu 

