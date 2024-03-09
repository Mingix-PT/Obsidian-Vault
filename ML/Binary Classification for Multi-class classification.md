### One-vs-one
- Xây dựng 1 bộ binary classifier cho mỗi 1 cặp classes -> cần $\frac{n(n-1)}{2}$ bộ
- Khi có 1 dữ liệu mới, đưa nó vào toàn bộ các bộ classifier trên
	- Fitting: xem dữ liệu được phân vào class nào nhiều nhất (major voting) -> phân vào đó
	- Logistic: tính tổng xác suất sau mỗi bộ classifier
- Nhược điểm: Số lượng classifier lớn, không lợi tính toán và bộ nhớ

### Hierarchical (phân tầng)
- Ý tưởng: Phân các classifier thành nhiều các mức độ ưu tiên, phân chia các cặp giống nhau
- Nhược điểm