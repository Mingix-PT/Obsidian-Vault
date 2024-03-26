# Tổng quan
- Sử dụng cho bài toán classification có rất nhiều chiều
- 1 trong các phương pháp tốt nhất cho phân lớp văn bản

# Kiến thức toán
- Khoảng cách từ 1 điểm -> 1 mặt phẳng$$\frac{|w_{1}x_{0}+ w_{2}y_{0}+w_{3}z_{0}+b|}{\sqrt{w_{1}^{2}+w_{2}^{2} + w_{3}^{2}}}$$ $$\frac{|\mathbf{w^{T}x_{0}}+b|}{||\mathbf{w}||_{2}}$$
# Bài toán
![[Pasted image 20240326222644.png]]

Có thể có vô số mặt phân chia -> chọn mặt nào?
Chọn đường 1 cách _văn minh_ và _công bằng_:

![[Pasted image 20240326222723.png]]

-> SVM

# Bài toán tối ưu
## Tuyến tính
Cần tìm mặt $\mathbf{w^{T}x}+b$ để phân chia 2 class: 1 và -1
Khoảng cách từ 1 điểm bất kì đến mặt phân chia:
$$\frac{y_{n}(\mathbf{w^{T}x_{n}}+b)}{||\mathbf{w}||_{2}}$$
Khi đó margin (lề) được tính là khoảng cách gần nhất từ 1 điểm tới mặt đó:$$\mathbf{margin}=\min_{n}\frac{y_{n}(\mathbf{w^{T}x_{n}}+b)}{||\mathbf{w}||_{2}}$$
Bài toán tối ưu trở thành:
$$(\mathbf{w},b)=\underset{\mathbf{w},b}{\mathbf{argmax}(\min_{n})}$$