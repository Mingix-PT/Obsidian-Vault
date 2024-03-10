### Định nghĩa
- Độ bất định, không chắc chắn của thông tin
- Kích cỡ mã hóa trung bình:
	- Dùng để so sánh độ hiệu quả của 2 bảng mã hóa
	- Tính bằng số bit trung bình được truyền đi mỗi lần truyền tin
	- $$everageBit = \sum_i^kp_in_i$$
	- Với $n_i$ là số bit dùng để mã hóa tín hiệu có tần suất $p_i$
Ví dụ:
![[Pasted image 20240310161602.png]]
	Everage bit 1 = $(10*1 + 20*1+40*2+30*2)/100=1.7$ bit
	Everage bit 2 = $(10*2+20*2+40*1+30*1)/100=1.1$ bit
	=> Bảng 2 tối ưu hơn bảng 1
- Công thức tính Entropy (kích cỡ mã hóa trung bình tối thiểu):
	- Cần tìm ra cách mã hóa tối ưu nhất
	- Với N tin nhắn, ta cần số bit mã hóa là $n=\log_2(N)$
	- Giả sử các tin nhắn có tần suất xuất hiện như nhau là $p=1/N$ 
	- $$n_p=\log_2N=\log_2\frac{1}{p}=-\log_2p$$
	- $$Entropy=-\sum_i^np_i*n_i=-\sum_i^np_i*\log_2(p_i)$$
- Tính chất:
	- Entropy dựa hoàn toàn vào xác suất
	- Khi các xác suất bằng nhau -> entropy đạt max -> khó dự đoán
### Cross Entropy
- Cross entropy giữa 2 phân phối $\mathbf{P}$ và $\mathbf{Q}$ được định nghĩa là:
$$CrossEntropy(P,Q)=-\sum_i^np_i*\log_2(q_i)$$
- Entropy của tín hiệu này có phân phối P (tính kì vọng dựa vào P) nhưng lại được mã hóa dựa vào phân phối Q.
- Tính chất:
	- Không đối xứng
	- Minimum <=> P == Q
	- Rất nhạy cảm với sự sai khác của $p_i$ và $q_i$
	
### Kullback-Leibler Divergence
- Dùng để đo tổn thất khi ước lượng, xấp xỉ 1 phân phối P bằng phân phối Q
- Công thức: $$
\begin{aligned}
D_{KL}(P||Q)&=CrossEntropy(P,Q)-Entropy(P)
\\
&=-\sum_i^np_i*\log_2(q_i)+\sum_i^np_i*\log_2(p_i) \\
&=\sum_i^np_i*\log_2\frac{p_i}{q_i}
\end{aligned}
$$
- Tính chất:
	- Không đối xứng
	- Rất nhạy cả, với sự sai khác giữa $p_i$ và $q_i$
	- Trong ML, tối ưu hàm KL_Divergence tương đương tối ưu hàm CrossEntropy
