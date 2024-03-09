Ý tưởng: Cứ làm, sai đâu sửa đấy, cuối cùng sẽ thành công

Bài toán: Xây dựng 1 classifier từ dữ liệu của 2 tập được gán nhãn cho trước -> dự đoán nhãn của các dữ liệu mới

	2 chiều: đường thẳng
	3 chiều: mặt phẳng
	4 chiều trở lên: đường phẳng

# PLA
Ý tưởng: Xuất phát từ 1 nghiệm dự đoán, qua các vòng lặp -> vị trí tốt hơn => nghiệm

Giả sử có nhãn __y__ = [y1, y2, ..., yN] với
			$y_i=1$    nếu xi thuộc class 1
			$y_i=-1$        xi thuộc class 2  
Tại 1 thời điểm, giả sử tìm được đường phẳng có phương trình:
$$f_w(x) = w_1x_1 + ... + w_dx_d + w_0$$
$$= w^{T}x$$
![[Pasted image 20240306172527.png]]

Các điểm cùng 1 phía sẽ làm hàm $f_w(x)$ mang cùng dấu => Giả sử xanh là (+) còn đỏ là (-), nhãn của mỗi điểm sẽ là:

$label(x) = 1$ if $w^{T}x\ge 0$ , otherwise -1

hay $label(x)=sgn(w^Tx)$
với sgn(0) = 1

### Hàm mất mát
Đếm số lượng điểm bị misclassified:
$$J_1(\mathbf{w})=\sum_{x\in M}(-y_isgn(w^Tx_i))$$
Với M là tập các điểm bị misclassified
Hàm trên khó tối ưu do nó rời rạc theo w

$$J(w)=\sum_{x\in M}(-y_iw^Tx_i)$$
Hàm trên trừng phạt các điểm lấn sâu sang lãnh thổ lớp kia nặng hơn hàm trên, ngoài ra hàm liên tục theo w nên tính đạo hàm đơn giản
Với 1 điểm dữ liệu $\mathbf{x_i}$ bị misclassified, hàm mất mát trở thành:
$$J(\mathbf{w};\mathbf{x_i};y_i)=-y_i\mathbf{w^T}\mathbf{x_i}$$
Đạo hàm:
$$\nabla_\mathbf{w}J(\mathbf{w};\mathbf{x_i};y_i)=-y_i\mathbf{x_i}$$
Sử dụng [Gradient Descent](Gradient%20Descent) để tối ưu:
$$\mathbf{w} = \mathbf{w} + \eta y_i\mathbf{x_i} $$
Chọn learning rate $\eta = 1$ ta có:
$$\mathbf{w} = \mathbf{w} + y_i\mathbf{x_i} $$
Xét:
$$\mathbf{w}_{t+1}^T\mathbf{x}_i = (\mathbf{w}_{t} + y_i\mathbf{x}_i)^T\mathbf{x}_{i} \newline  
= \mathbf{w}_{t}^T\mathbf{x}_i + y_i ||\mathbf{x}_i||_2^2$$
Dễ thấy $\mathbf{w}_{t+1}^T\mathbf{x}_i > \mathbf{w}_{t}^T\mathbf{x}_i$ vì $y_i ||\mathbf{x}_i||_2^2 = ||\mathbf{x}_i||_2^2 > 0$ khi $y_i = 1$
=> Đường thẳng tiến về phía làm $\mathbf{x_i}$ được phân lớp đúng
Điều ngược lại cũng đúng khi $y_i=-1$

### Tóm tắt
1. Chọn ngẫu nhiên một vector hệ số __$\mathbf{w}$__ với các phần tử gần 0.
2. Duyệt ngẫu nhiên qua từng điểm dữ liệu $\mathbf{x_i}$:
    - Nếu $\mathbf{x_i}$ được phân lớp đúng, tức $sgn(\mathbf{w}^T\mathbf{x}_i)=y_i$, chúng ta không cần làm gì.
    - Nếu $\mathbf{x_i}$ bị misclassifed, cập nhật $\mathbf{w}$ theo công thức: $\mathbf{w} = \mathbf{w} + y_i\mathbf{x_i}$
3. Kiểm tra xem có bao nhiêu điểm bị misclassifed. Nếu không còn điểm nào, dừng thuật toán. Nếu còn, quay lại bước 2.

### Mô hình Neural Network
Hàm số xác định class của Perceptron $label(\mathbf{x})=sgn(\mathbf{w^T x})$ có thể được mô tả như hình vẽ (được gọi là network) dưới đây:
![[Pasted image 20240308232022.png]]

- Input: các node màu xanh lá cây với node $x_0$ = 1 (luôn luôn). Đôi khi node $x_0$ được ẩn đi
- Weight: trọng số, $w_0 -> w_n$ được gán lên các mũi tên
- Output: Node $y =sgn(z)$ (Kí hiệu chữ Z ngược là đồ thị hàm $sgn$) còn được gọi là _activation function_ 
- Các neural network có thể có nhiều node ở output tạo thành _output layer_ hoặc có thể thêm nhiều layer trung gian ở giữa, được gọi là _hidden layer_
- Network lớn -> giản lược thành hình bên phải, ẩn node _$z$_ và node $x_0$ = 1
- Nếu thay _activation function_ bởi $y=z$, ta có Neural Network của Linear Regeression:
![[Pasted image 20240308232748.png]]

### Pocket Algorithm
Một cách tự nhiên, nếu có một vài _nhiễu_, ta sẽ đi tìm một đường thẳng phân chia hai class sao cho có ít điểm bị misclassified nhất. Việc này có thể được thực hiện thông qua PLA với một chút thay đổi nhỏ như sau:

1. Giới hạn số lượng vòng lặp của PLA.
2. Mỗi lần cập nhật nghiệm $\mathbf{w}$ mới, ta đếm xem có bao nhiêu điểm bị misclassified. Nếu là lần đầu tiên, giữ lại nghiệm này trong _pocket_ (túi quần). Nếu không, so sánh số điểm misclassified này với số điểm misclassified của nghiệm trong _pocket_, nếu nhỏ hơn thì _lôi_ nghiệm cũ ra, đặt nghiệm mới này vào.

Thuật toán này giống với thuật toán tìm phần tử nhỏ nhất trong 1 mảng.