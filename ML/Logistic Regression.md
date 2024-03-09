Đầu ra dưới dạng xác suất
Thường sử dụng cho các bài toán classification

Đầu ra có dạng như sau:
$$f(\mathbf{x})=\theta(\mathbf{w^T x})$$
Trong đó $\theta$ được gọi là logistic function


### Bài toán

![[Pasted image 20240308235203.png]]

Cần tính xác suất y theo x
### Sigmoid function
$$\sigma(s)=\frac{1}{1+e^{-s}}$$
Được sử dụng nhiều nhất
Các tính chất:
- Bị chặn trong khoảng (0;1)
- Giới hạn:
$$\lim_{s\rightarrow -\infty}\sigma(s) =0;\lim_{s\rightarrow \infty}\sigma(s) =1 $$
- Đạo hàm:
$$
\begin{aligned}
\sigma(s)'=\frac{e^{-s}}{(1+e^{-s})^2}
&=\frac{1}{1+e^{-s}}.\frac{e^{-s}}{1+e^{-s}}\\
&=\sigma(s)(1-\sigma(s))
\end{aligned}
$$

### Hàm mất mát
Giả sử xác suất 1 điểm dữ liệu $\mathbf{x}$ rơi vào class 1 là $f(\mathbf{w^T x})$ và rơi vào class 0 là $1-f(\mathbf{w^T x})$
Ta có:
$$
\begin{aligned}
P(y_i=1|\mathbf{x_i;w}) =\;\;\;\;\;\,\, f(\mathbf{w^T x})\\
P(y_i=0|\mathbf{x_i;w}) =1- f(\mathbf{w^T x})
\end{aligned}
$$
Mục tiêu: Tìm $\mathbf{w}$ sao cho $f(\mathbf{w^T x}$ ) càng gần 1 với các dữ liệu thuộc class 1 và càng gần 0 cho các dữ liệu thuộc class 0
Đặt
$$z_i=f(\mathbf{w^T x})$$
Viết gộp hai biểu thức trên:
$$P(y_i|\mathbf{x_i;w})=z^{y_i}_i(1-z_i)^{1-y_i}$$
Cần xác suất trên đạt giá trị cao nhất.
Xét toàn bộ training set: Ta cần tìm $\mathbf{w}$ để xác suất $P=(\mathbf{y|X;w})$ đạt giá trị lớn nhất, hay:
$$\mathbf{w}=\underset{\mathbf{w}}{\operatorname{argmax}} = P(\mathbf{y|X;w})$$
Đây là bài toán __maximum likelihood__ 
Giả sử các điểm dữ liệu độc lập với nhau:
$$
\begin{aligned}
P(\mathbf{y|X;w})&=\prod^N_{i=1}P(y_i|\mathbf{x_i;w})\\
&=\prod^N_{i=1}z_i^{y_i}(1-z_i^{y_i})^{1-y_i}
\end{aligned}
$$
Trực tiếp tối ưu hàm trên theo $\mathbf{w}$ không đơn giản, ngoài ra dễ dẫn đến sai số do các xác suất < 1, tích sẽ rất nhỏ.
Lấy logarit cơ số e để chuyển tích thành tổng, ta được hàm sau:

$$
\begin{aligned}
J(\mathbf{w})&=-\log P(\mathbf{y|X;w}) \\
&=-\sum_{i=1}^{N}(y_i\log z_i+(1-y_i)\log(1-z_i))
\end{aligned}
$$

Hàm bên phải được gọi là __cross entropy__, thường sử dụng để đo khoảng cách giữa 2 phân phối.
__Lưu ý__: log trong ML thường để kí hiệu logarit của e
Đặt $s=\mathbf{w^T x}$, $z=f(s)$ 
Ta tìm được:
$$z=\frac{1}{1+e^{-s}}=\sigma(s)$$
Sử dụng [Stochastic Gradient Descent](Gradient%20Descent#Stochastic%20Gradient%20Descent) để tối ưu:
$$\frac{\partial J(\mathbf{w;x_i};y_i)}{\partial\mathbf{w}}=(z_i-y_i)\mathbf{x_i}$$
Công thức cập nhật:
$$\mathbf{w} = \mathbf{w} + \eta(y_i-z_i)\mathbf{x_i}$$

### Một vài tính chất
- Phù hợp với classification hơn fitting
- Boundary luôn tuyến tính
- Phù hợp với dữ liệu gần linearly separable, không phù hợp non-linear
- Yêu cầu các dữ liệu độc lập với nhau
- Neural Network:
![[Pasted image 20240309101656.png]]
