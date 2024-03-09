### Mục đích

Các bộ phận:

![[Pasted image 20240229073213.png]]
	- Actors
	- Use cases
	- Đặc tả use case
	- Từ điển thuật ngữ
	- Đặc tả phụ trợ

### Use case diagram
- Lợi ích của use case diagram:
	- Giao tiếp
	- Xác định
	- Kiểm chứng
- Các thành phần chính:
	- Actor: 
		- Bất kì thứ gì tương tác với phần mềm (nằm ngoài phần mềm).
		- Khi vẽ cần vẽ actor ở ngoài khung hình chữ nhật (phần mềm).
		- Là 1 nhóm người dùng.
		- 1 người cụ thể có thể thuộc nhiều actor.
		- **Là 1 danh từ.**
	- Use case: 
		- 1 chuỗi các sự kiện thực hiện bởi phần mềm, cung cấp được 1 giá trị quan sát được cho 1 actor.
		- Mô hình một cuộc giao tiếp giữa 1 hay nhiều actor với phần mềm.
		- __Là 1 động từ.__
- Mối quan hệ
	- Giữa các tác nhân:
		- Generalization
	- Giữa tác nhân và use case:
		- Association: 
			- 1 use case có thể liên kết với 1 hoặc nhiều actor. Tuy nhiên khi vẽ với nhiều actor cần thống nhất mũi tên sử dụng khi xét từng cặp hay xét cả use case.
		- ![[Pasted image 20240229092308.png]]
			- Khi có nhiều actor có thể dùng cùng 1 use case, ta có thể tạo 1 abstract user A, nối A với use case đó xong nối các actor generalization với A.
	- Giữa các use case (__không nên lạm dụng__):
		- Generalization
			- Use case con kế thừa hành vi và ý nghĩa của use case cha, có thể thêm hoặc ghi đè hành vi của cha.
			- Nếu use case con có thể thay thế use case cha hoàn toàn -> đúng.
		- include
			- Use case bắt buộc bao gồm các use case khác, use case được include không phải 1 use case hoàn chỉnh, không thể đứng độc lập
			- Use case to gọi là use case cơ sở, use case được include gọi là use case được bao hàm.
			- Thường sử dụng khi 2 hay nhiều use case có các bước hay use case chung để tránh lặp lại.
		- extend
			- Diễn biến: A -> B -> C, thể hiện thứ tự thực hiện use case
			- Use case to gọi là use case cơ sở, use case extend gọi là use case mở rộng.
			- Use case cơ sở có thể đứng 1 mình tuy nhiên trong vài trường hợp có thể mở rộng thêm.
- Cách phân cấp UC
	1. Vẽ UCD tổng quan chứa các composite use case (nhóm các use case cùng chủ đề)
	2. Vẽ UCD phân rã: phân tách từng composite use case thành các use case nhỏ hơn và vẽ từng UCD tương ứng với từng composite use case.
### Đặc tả use case
Mỗi 1 use case cần đi kèm 1 đặc tả cho use case đó
Đặc tả use case bao gồm:
- Code
- Name
- Brief Description
- Flow of Events: Kịch bản, biểu diễn bằng bảng
	![[Pasted image 20240307084646.png]]
	- Có 1 flow chính
	- Có vài flow phụ gồm 3 loại
		- Regular variants
		- Odd cases
		- Exceptional flows: gặp lỗi cần xử lý
	- Cần đặc tả chi tiết, tránh sơ sài
- Relationship
- Activity diagrams
![[Pasted image 20240307084722.png]]
![[Pasted image 20240307085034.png]]
- Use-case diagrams
- Special requirements
- Pre-conditions (tiền điều kiện)
- Post-conditions (hậu điều kiện)

### Từ điển thuật ngữ
### Đặc tả hỗ trợ
