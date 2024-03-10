PLA có thêm các _hidden layer_ làm layer trung gian
![[Pasted image 20240310233536.png]]

### Các khái niệm
#### Số layer trong MLP
là $L$, bằng số hidden layer + 1

#### Unit: Là 1 node hình tròn trong 1 layer. Có 3 loại: input unit, hidden unit, output unit.
- Đầu vào: $z$
- Đầu ra của unit thứ $i$ trong layer thứ $l$ là $a^{(l)}_i$ 
- Số unit trong layer thứ $l$ (không tính bias) là $d^{(l)}$
- Vector biểu diễn output của layer thứ $l$ là $a^{(l)}$ 
- Weights và Biases
	- Có $L$ ma trận trọng số cho MLP có $L$ layer: $\mathbf{W}^{(l)}\in R^{d^{(l-1)}\times d^{(l)}}$ thể hiện kết nối từ layer $l-1$ đến layer $l$ (layer input coi là layer 0)
	- Bias của layer thứ $l$ ký hiệu là $\mathbf{b}^{(l)}\in R^{d^{(l)}}$ 
	- Tập hợp các weight và bias: $\mathbf{W,\;b}$ 
- Activation function
	- 