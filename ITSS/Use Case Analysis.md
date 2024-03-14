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
- Lớp điều khiển: 
	- Đứng ở giữa
	- Cung cấp các thao tác điều khiển
	- Nên có ít nhất 1 lớp điều khiển cho mỗi 1 use case
- Lớp thực thể: 
	- Chứa thông tin của thực thể
	- 