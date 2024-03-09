### One-vs-one
- Xây dựng 1 bộ binary classifier cho mỗi 1 cặp classes -> cần $\frac{n(n-1)}{2}$ bộ
- Khi có 1 dữ liệu mới, đưa nó vào toàn bộ các bộ classifier trên
	- Fitting: xem dữ liệu được phân vào class nào nhiều nhất (major voting) -> phân vào đó
	- Logistic: tính tổng xác suất sau mỗi bộ classifier
- Nhược điểm: Số lượng classifier lớn, không lợi tính toán và bộ nhớ

### Hierarchical (phân tầng)
- Ý tưởng: Phân các classifier thành nhiều các mức độ ưu tiên, phân chia các cặp giống nhau
- Nhược điểm: 1 classifier sai -> kết quả chắc chắn sai

### Binary coding
- Mã hóa output mỗi class = 1 số nhị phân
	- 4 class: 00, 01, 10, 11
- Số lượng binary classifiers là $m=\lceil\log_2(C)\rceil$ với $\lceil a\rceil$ là số nguyên nhỏ nhất không nhỏ hơn a. Dùng $m$ bộ để phân $m$ bit
- Nhược điểm: 
	- Sai 1 bit -> sai toàn bộ
	- Nếu số class không phải là $2^n$ thì có thể mã nhị phân nhận được k tương ứng với class nào

### One-vs-rest (One-hot-coding)
- Xây dựng $C$ classifier tương ứng với $C$ class
- Classifier thứ $i$ sẽ phân biệt class $i$ và not class $i$ hoặc xác suất để 1 điểm rơi vào class $i$
- Mã hóa dưới dạng nhị phân: 00..01..00 (bit thứ $i$ là 1 chỉ ra điểm đó thuộc class $i$)

### Biểu diễn Neural Network
![[Pasted image 20240309224503.png]]

![[Pasted image 20240309224511.png]]

