PLA có thêm các _hidden layer_ làm layer trung gian
![[Pasted image 20240310233536.png]]

### Các khái niệm cơ bản
#### Số layer
$L$, bằng số hidden layer + 1

#### Unit: 
Là 1 node hình tròn trong 1 layer. 
Có 3 loại: input unit, hidden unit, output unit.
- Đầu vào: $z$
- Đầu ra của unit thứ $i$ trong layer thứ $l$ là $a^{(l)}_i$ 
- Số unit trong layer thứ $l$ (không tính bias) là $d^{(l)}$
- Vector biểu diễn output của layer thứ $l$ là $a^{(l)}$ 

#### Weights và Biases
- Có $L$ ma trận trọng số cho MLP có $L$ layer: $\mathbf{W}^{(l)}\in R^{d^{(l-1)}\times d^{(l)}}$ thể hiện kết nối từ layer $l-1$ đến layer $l$ (layer input coi là layer 0)
- Bias của layer thứ $l$ ký hiệu là $\mathbf{b}^{(l)}\in R^{d^{(l)}}$ 
- Tập hợp các weight và bias: $\mathbf{W,\;b}$ 

#### Activation function
- Mỗi output của 1 unit được tính dựa vào công thức: $$a_i^{(l)}=f(\mathbf{w}^{(l)T}a^{(l-1)}+b_i^{(l)})$$
- $f(.)$ là một non-linear activation function
- Viết dưới dạng vector: $$a^{(l)}=f(\mathbf{W}^{(l)T}a^{(l-1)}+\mathbf{b^{(l)}})$$
- Hàm sgn không được dùng trong MLP
- Hàm sigmoid và tanh ít được sử dụng do khi đầu vào có trị tuyệt đối lớn -> gradient rất gần 0 => các hệ số unit gần như k cập nhật
- Hàm ReLU (Rectified Linear Unit) $$f(s)=\max(0,s)$$được sử dụng rộng rãi vì hội tụ nhanh hơn các hàm trên. Trong thực nghiệm, mặc dù ReLU k có đạo hàm tại $s=0$, người ta định nghĩa ReLU'(0) = 0

#### Lưu ý:
- Output layer nhiều khi không có activation function mà sử dụng giá trị đầu vào của mỗi unit -> hàm _identity_
- Với các bài toán classification, output layer thường là layer [[Softmax Regression]]
- Trong cùng 1 network, activation như nhau thường được sử dụng -> tính toán đơn giản

### Backpropagation
Là bước cập nhật lại các weight và bias của từng layer