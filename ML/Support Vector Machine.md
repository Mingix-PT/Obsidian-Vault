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
$$(\mathbf{w},b)
=\underset{\mathbf{w},b}{\mathbf{argmax}}(\min_{n} \frac{y_{n}(\mathbf{w^{T}x_{n}}+b)}{||\mathbf{w}||_{2}})
=\underset{\mathbf{w},b}{\mathbf{argmax}}(\frac{1}{||\mathbf{w}||_{2}}\min_{n}y_{n}(\mathbf{w^{T}x_{n}}+b))$$
Với mọi n:
$$y_{n}(\mathbf{w^{T}x_{n}}+b) \ge 1$$
![[Pasted image 20240326224121.png]]
Dễ thấy hàm mục tiêu lồi, hàm ràng buộc là tuyến tính -> hàm lồi
=> Bài toán lồi => Nghiệm là duy nhất

Tuy nhiên có thể phức tạp -> số chiều d lớn => Giải bài toán đối ngẫu [[Duality]]

# Bài toán đối ngẫu SVM

![[Pasted image 20240327002114.png]]
![[Pasted image 20240327002131.png]]
![[Pasted image 20240327002152.png]]
![[Pasted image 20240327002227.png]]
Cuối cùng:![[Pasted image 20240327002314.png]]
Vậy bài toán đối ngẫu có dạng:

![[Pasted image 20240327002336.png]]

Từ điều kiện KTT, ta rút ra được:
![[Pasted image 20240327002604.png]]
Như vậy các điểm thỏa mãn $\mathbf{w^{T}x_{n}}+b=y_{n}=\pm1$ là các điểm gần mặt phân chia nhất
-> Các điểm (vector) thỏa mãn (14) được gọi là _Support Vectors_
Tính wT:
![[Pasted image 20240327003327.png]]
Tính b:
![[Pasted image 20240327003339.png]]
là trung bình cộng của mọi cách tính b
Vậy mặt phân chia của ta có phương trình:
![[Pasted image 20240327003425.png]]
