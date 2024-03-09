### One-vs-rest
Sử dụng với [[Logistic Regression]]:
$$a_i=sigmoid(z_i)=sigmoid(\mathbf{w_i^T x})$$
### Soft-max function
$$a_i=\frac{\exp(z_i)}{\sum_{j=1}^{C}\exp(z_j)}$$
Hàm trên thỏa mãn:
- $a_i$ dương và tổng chúng bằng 1
- Hàm exp c