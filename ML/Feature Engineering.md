### Mô hình chung cho các bài toán ML

![[Pasted image 20240309105337.png]]

### Training Phase
Cần thiết kế 2 khối xanh lục ở trên
#### Feature Extractor
##### Đầu vào
- Raw training input:
	- Là tất cả các thông tin ta biết về dữ liệu
		- Ảnh: giá trị từng pixel
		- Văn bản: từng từ, câu
		- File âm thanh: đoạn tín hiệu
	- Thường không ở dạng vector, không có cùng số chiều hay cùng nhưng quá lớn
- Output của training set (optional)
	- Chỉ supervised có (nhiều khi cũng không sử dụng)
- Prior knowledge about data (optional)
##### Đầu ra
- Dữ liệu thô ban đầu -> dữ liệu phù hợp

Sau khi học được feature extracor thì ta thu được extracted features cho raw input data -> huấn luyện các thuật toán ở sau

##### Main algorithm
Khi có được _extracted features_ rồi, chúng ta sử dụng những thông tin này cùng với (optional) _training output_ và (optional) _prior knowledge_ để tạo ra các mô hình phù hợp

### Testing phase
Với _raw input_ mới, ta sử dụng feature extractor đã tạo được ở trên (tất nhiên không được sử dụng _output_ của nó vì _output_ là cái ta đang đi tìm) để tạo ra feature vector tương ứng. Feature vector được đưa vào _main algorithm_ đã được học ở training phase để dự đoán _output_