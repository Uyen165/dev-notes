# Thuật toán sắp xếp chọn - Selection Sort
Selection Sort cũng là một thuật toán sắp xếp đơn giản - cùng nhóm với Bubble Sort. Ý tưởng của Selection Sort khá đơn giản, chúng hoạt động bằng cách:
- Giả sử bạn có một đống thẻ số lộn xộn
- Ở mỗi bước, bạn tìm phần tử nhỏ nhất (hoặc lớn nhất nếu muốn sắp xếp giảm dần) trong phần còn lại của mảng
- Đem phần tử đó đổi chỗ với phần tử ở vị trí đầu tiên của phần chưa sắp xếp
- Lặp lại cho đến khi hết mảng

## Tính chất bất biến - Invariant
Sau i lần lặp, i phần tử đầu tiên đã đúng vị trí. Sau khi tìm min/max và đổi chỗ, phần tử đó đã ko cần đổi lại nữa. Nó giống như bạn đang xây 1 hàng gạch, mỗi lần đặt một viên đúng chỗ, không cần động lại nữa

### Độ phức tạp - Complexity & Tính ổn định - Stable
- Độ phức tạp: Nó luôn duyệt hết phần chưa sắp xếp nên tất cả đều là O(n^2) về số so sánh. Dẫn đến việc không tối ưu nếu mảng đã sắp xếp ( vì nó vẫn duyệt hết)
- Tính ổn định: Selection Sort không ổn định. Bởi nó luôn swap min/ max với đầu phần chưa sắp xếp, bất kể thứ tự bằng. Ví dụ: [4a, 4b, 3] sắp xếp tăng dần, với 4a = 4b (chỉ khác nhãn). Sau khi thực hiện, nó sẽ là [3, 4b, 4a] --> mất tính ổn định

#### Code Python: Sắp xếp tăng dần
```python
def tangdan(lst):
    n = len(lst)
    for i in range(n - 1): #Khi da sap xep duoc n - 1 phan tu dau, phan con lai chac chan dung, nen chi can n - 1 vong
        min_idx = i #i la de luu vi tri nho nhat sau moi vong lap, voi vong lap dau tien, no mac dinh la gt dau tien
        for j in range(i + 1, n):
            if lst[j] < lst[min_idx]:
                min_idx = j
        lst[i], lst[min_idx] = lst[min_idx], lst[i] #Hoan doi phan tu nho nhat ve dung cho, sau khi doi, phan tu i da o dung vi tri nen k can dung vao nua
    return lst
if __name__ == '__main__':
    l = list(map(int, input().split()))
    print(tangdan(l))
```
