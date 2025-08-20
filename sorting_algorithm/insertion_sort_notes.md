# Insertion Sort - Thuật toán sắp xếp chèn
Insertion Sort là một thuật toán sắp xếp đơn giản, ý tưởng hoạt động của chúng như sau:
- Giả sử bạn có một bộ bài rời rạc trên tay
- Bạn lấy từng lá bài từ bộ bài chưa sắp xếp, rồi chèn vào vị trí đúng trong phần đã sắp xếp (bắt đầu từ trái)
- Lặp lại cho đến khi hết mảng

## Cách thuật toán hoạt động trong code
Nếu bạn thấy ý tưởng trên vẫn trông thật khó hiểu, vậy hãy thử thực hiện với một danh sách số: [5, 2, 8, 1, 9]. Giả sử bạn muốn sắp xếp tăng dần, vậy đây là cách hoạt động:
- Bắt đầu từ phần tử thứ 2 (vì phần tử thứ nhất được coi là "đã sắp xếp")
- So sánh phần tử đó với các phần tử đứng trước nó
- Nếu phần tử phía trước lớn hơn, dịch chuyển phần tử đó sang phải để nhường chỗ
- Chèn phần tử đang xét vào vị trí phù hợp
- Lặp lại cho đến khi toàn bộ danh sách được sắp xếp

### Tính chất bất biến - Invariant & Một số điểm lưu ý
- Phần bên trái của vị trí hiện tại luôn được sắp xếp
- Ưu điểm của thuật toán: Hiệu quả với mảng gần như đã sắp xếp (O(n)) và giữ thứ tự phần tử bằng nhau (Stable)
- Nhược điểm: Duyệt nhiều, O(n^2) thời gian với mảng ngẫu nhiên

#### Code Python
```python
#Insertion Sort - Sap xep chen

#Sap xep tang dan
def tang(lst):
    n = len(lst)
    for i in range(1, n):
        key = lst[i]
        j = i - 1
        while j >= 0 and lst[j] > key:
            lst[j + 1] = lst[j]
            j -= 1
        lst[j + 1] = key
    return lst
if __name__ == '__main__':
    l = list(map(int, input().split()))
    print(tang(l))
```
Chúc các bạn học tốt!
