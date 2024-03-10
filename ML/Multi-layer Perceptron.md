PLA có thêm các _hidden layer_ làm layer trung gian
![[Pasted image 20240310233536.png]]

- Các khái niệm
	- Số layer trong MLP là $L$, bằng số hidden layer + 1
	- Unit: Là 1 node hình tròn trong 1 layer. Có 3 loại: input unit, hidden unit, output unit.
		- Đầu vào: $z$
		- Đầu ra của unit thứ $i$ trong layer thứ $l$ là $a^{(l)}_i$ 
		- Số unit trong layer thứ $l$ (không tính bias) là $d^{(l)}$
		- Vector biểu diễn output của layer thứ $l$ là $a^{(l)}$ 