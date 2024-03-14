![[Pasted image 20240314073716.png]]
# Tìm lớp phân tích 
![[Pasted image 20240314074943.png]]

- Lớp biên: 
	- Tác nhân muốn tương tác vs hệ thống -> qua lớp biên
	- 3 loại:
		- Lớp UI (user interface)
			- Thường có "Form" hoặc "View" trong tên
		- Lớp SI (system interface)
		- Lớp DI (device interface)
	- Chưa cần quan tâm chi tiết
	- Mỗi 1 use case thường có 1 lớp biên
- Lớp điều khiển: 
	- Đứng ở giữa
	- Cung cấp các thao tác điều khiển
	- Nên có ít nhất 1 lớp điều khiển cho mỗi 1 use case
- Lớp thực thể: 
	- Chứa thông tin của thực thể

# Tìm hành vi cho lớp phân tích
- Chỉ quan tâm hành vi, chưa quan tâm thuộc tính
	- Lớp biên: Hành vi với tác nhân
	- Lớp thực thể: Hành vi với dữ liệu
	- Lớp điều khiển: Hành vi với use case
- Phân nhiệm vụ

# Biểu đồ tương tác
## Biểu đồ trình tự
- Nhấn mạnh thứ tự thời gian của thông điệp
- Cấu trúc:![[Pasted image 20240314083817.png]]
- Trả về kết quả: nét đứt
- Trả về thông điệp: nét liền

## Biểu đồ giao tiếp
- Nhấn mạnh vào tương tác![[Pasted image 20240314084948.png]]
- 