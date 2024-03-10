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
[Cross Entropy](Entropy#Cross%20Entropy) giữa hai phân phối $\mathbf{p}$ và $\mathbf{q}$ được định nghĩa là:
$$H(\mathbf{p,q})=\mathbf{E_p|-\log q|}$$
Với p và q rời rạc: $$H(\mathbf{p,q})= -\sum\limits_{i}^{C}p_{i}\log q_i$$
p là đầu ra thực sự, q là đầu ra dự đoán

Hàm mất mát giữa đầu ra dự đoán và đầu ra thực sự của $\mathbf{x_i}$ là: $$J(\mathbf{W;x_i,y_i})=-\sum^{C}_{j=1}y_{ji}\log(a_{ji})$$
Hàm mất mát cho Softmax Regression:
$$
\begin{aligned}
J(\mathbf{W;X;Y})
&=
-\sum_{i=1}^{N}\sum_{j=1}^{C}y_{ji}\log(a_{ji})
\\
&= -\sum_{i=1}^{N}\sum_{j=1}^{C}y_{ji}\log(\frac{\exp(\mathbf{w^{T}_{j}x_{i}})}{\sum_{k=1}^{C}\exp(\mathbf{w^{T}_{k}x_{i}})})
\end{aligned}
$$
Tối ưu sử dụng [Stochastic Gradient Descent](Gradient%20Descent#Stochastic%20Gradient%20Descent) cho mỗi cặp dữ liệu $(\mathbf{x_i;y_i})$:
$$
\begin{aligned}
J_i(\mathbf{W})
&=J(\mathbf{W;x_i;y_{i})}
\\
&=-\sum_{j=1}^{C}y_{ji}\log(\frac{\exp(\mathbf{w^{T}_{j}x_{i}})}{\sum_{k=1}^{C}\exp(\mathbf{w^{T}_{k}x_{i}})})
\\
&=-\sum\limits_{j=1}^{C}(y_{ji}\mathbf{w^{T}_{j}x_{i}-y_{ji}\log(\sum\limits^{C}_{k=1}\exp(\mathbf{w^{T}x_{i}})})
\\
&=-\sum\limits_{j=1}^{C}y_{ji}\mathbf{w^{T}_{j}x_{i}}+\log(\sum\limits^{C}_{k=1}\exp(\mathbf{w^{T}x_{i})}
\end{aligned}
$$
Có được dòng cuối do $\sum\limits^{C}_{j=1}y_{ji}=1$ vì nó là tổng các xác suất
Có: $$\frac{\partial J_i(\mathbf{W})}{\partial W}=[
\frac{\partial J_i(\mathbf{W})}{\partial \mathbf{w_1}},
\frac{\partial J_i(\mathbf{W})}{\partial \mathbf{w_2}},
...,
\frac{\partial J_i(\mathbf{W})}{\partial \mathbf{w_C}}]$$
Trong đó gradient từng cột tính như sau:


