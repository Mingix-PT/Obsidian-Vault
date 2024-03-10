### One-vs-rest
Sử dụng với [[Logistic Regression]]:
$$a_i=sigmoid(z_i)=sigmoid(\mathbf{w_i^T x})$$
### Soft-max function
$$a_i=\frac{\exp(z_i)}{\sum_{j=1}^{C}\exp(z_j)}$$
Hàm trên thỏa mãn:
- $a_i$ dương và tổng chúng bằng 1
- Hàm exp cho $z_i$ thỏa mãn:
	- Đồng biến
	- Mượt -> dễ đạo hàm
	- Dương

Ta có thể giả sử rằng:
$$P(y_k=i|\mathbf{x_k};W)=a_i$$
### Neural Network
![[Pasted image 20240309230139.png]]

### Cải tiến 
Khi một trong các $z_i$ quá lớn, tính $\exp(z_i)$ có thể bị tràn số -> ảnh hưởng kết quả
Khắc phục: hàm softmax stable
$$
\begin{aligned}
a_i=\frac{\exp(z_i)}{\sum_{j=1}^C\exp(z_j)}
&=\frac{\exp(-c)\exp(z_i)}{\exp(-c)\sum_{j=1}^C\exp(z_j)}\\
&=\frac{\exp(z_i-c)}{\sum_{j=1}^C\exp(z_j-c)}
\end{aligned}
$$
Trong thực nghiệm, hay chọn $c=\max \mathbf{x}_iz_i$ 

### Hàm mất mát và tối ưu
#### Entropy
- ĐN: Độ bất định, không chắc chắn của thông tin
- Kích cỡ mã hóa trung bình:
	- Dùng để so sánh độ hiệu quả của 2 bảng mã hóa
	- Tính bằng số bit trung bình được truyền đi mỗi lần truyền tin
Ví dụ:
![[Pasted image 20240310161602.png]]
	Average bit 1 = $(10*1 + 20*1+40*2+30*2)/100=1.7$ bit
	Average bit 2 = $(10*2+20*2+40*1+30*1)/100=1.1$ bit
	=> Bảng 2 tối ưu hơn bảng 1
	- Kích cỡ mã hóa trung bình tối thiểu
#### Cross Entropy
Cross entropy giữa 2 phân phối $\mathbf{p}$ và $\mathbf{q}$ được định nghĩa là:
$$H(\mathbf{p,q})=\mathbf{E_p|-\log q|}$$