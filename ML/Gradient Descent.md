Ý tưởng: Xuất phát từ 1 điểm coi là gần nghiệm bài toán, dùng phép lặp -> điểm cần tìm f'(x) = 0
# GD cho hàm 1 biến
$$ x_{t+1} = x_t - \eta f'(x_t)$$
	Trong đó $\eta$ là một số dương, được gọi là learning rate (tốc độ học)
	Lựa chọn $\eta$ rất quan trọng: 
		- $\eta$ nhỏ: Hội tụ chậm, lâu về đích
		- $\eta$ lớn: Tiến đến đích nhanh nhưng khó hội tụ vì bước nhảy lớn
	=> Chọn $\eta$ tại mỗi bước
	
# GD cho hàm nhiều biến
	$$\theta_{t+1} = \theta_{t} - \eta\nabla_\theta f(\theta_t)$$
# Cách tính xấp xỉ đạo hàm
$$f'(x) = \lim_{\varepsilon\to0}\frac{f(x+\varepsilon)-f(x)}{\varepsilon}$$ $$f'(x)\approx\frac{f(x+\varepsilon)-f(x-\varepsilon)}{2\varepsilon}$$
	với $\varepsilon$ < $10^{-6}$
	
# GD với momentum
Ý tưởng: suy nghĩ 1 cách vật lý, coi điểm xét là 1 viên bi lăn dốc, nếu lăn vào local minimum thì cần có đà để vượt lên lăn xuống global minimum
Đặt $v_t$ là độ dời của viên bi, vị trí mới của viên bi là:
$$\theta_{t+1} = \theta - v_t$$
Cần $v_t$ vừa mang thông tin độ dốc (đạo hàm) vừa mang thông tin của đà $v_{t-1}$ ($v_0=0$)
$$v_t=\gamma v_{t-1} + \eta \nabla_\theta J(\theta)$$
Ưu điểm: dễ tìm được global minimum hơn GD OG
Nhược điểm: 
- Hội tụ chậm hơn tại gần nghiệm
- Chi phí tính toán cao hơn

# Nesterov accelerated gradient (NAG)
Ý tưởng: dự đoán hướng đi tương lai, lấy gradient của điểm tiếp theo để tính độ dời của lần hiện tại
$$v_t=\gamma v_{t-1} +  \eta\nabla_\theta J(\theta-\gamma v_{t-1})$$
$$\theta_{t+1} = \theta_t - v_t$$

# Stochastic Gradient Descent
- Phù hợp với online learning
- Mỗi lần tối ưu hàm mất mát, ta chỉ tính cho 1 điểm trong toàn bộ dữ liệu --> nhanh, giảm bộ nhớ
- Khi thêm 1 điểm mới, ta chỉ cần tối ưu hàm mất mát thêm với điểm đó.
- Thứ tự chọn điểm dữ liệu mỗi epoch là ngẫu nhiên
- Có thể cải tiến lên: mỗi lần tối ưu ta chọn 1 vài điểm (thường là 50-100) -> mini-batch GD

# Điều kiện dừng
- Giới hạn số vòng lặp
	- Ưu điểm: Đảm bảo chương trình chạy không quá lâu
	- Nhược điểm: Có thể dừng trước khi tới đủ gần nghiệm
- So sánh gradient của nghiệm tại 2 lần liên tiếp
	- Nhược điểm: Việc tính đạo hàm có thể khó khăn, nhất là khi có quá nhiều dữ liệu
- So sánh giá trị hàm mất mát tại 2 lần liên tiếp
	- Nhược điểm: Có thể tại 1 điểm đồ thị hàm mất mát có dạng bằng phẳng nhưng không chứa local minimum -> sai
- So sánh nghiệm sau 1 vài lần cập nhật

