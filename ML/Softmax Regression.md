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
Khắc phục:
$$
\begin{aligned}
a_i=\frac{\exp(z_i)}{\sum_{j=1}^C\exp(z_j)}
&=\frac{\exp(-c)\exp(z_i)}{\exp(-c)\sum_{j=1}^C\exp(z_j)}\\
&=
\end{aligned}
$$