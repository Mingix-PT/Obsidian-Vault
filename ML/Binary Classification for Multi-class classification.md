### One-vs-one
- Xây dựng 1 bộ binary classifier cho mỗi 1 cặp classes -> cần $\frac{n(n-1)}{2}$ bộ => lớn, không lợi tính toán
- Khi có 1 dữ liệu mới, đưa nó vào toàn bộ các bộ classifier trên
	- Fitting: xem dữ liệu được phân vào class nào nhiều nhất (major voting) -> phân vào đó
	- Logistic: tính tổng xác suất sau mỗi bộ classifier

### Hierarchical (phân tầng)
