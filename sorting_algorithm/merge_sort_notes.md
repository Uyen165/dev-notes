# Merge Sort - Thuật toán sắp xếp trộn
Thuộc nhóm Thuật toán nhanh hơn và mang tính thực tế hơn 3 thuật toán Bubble Sort, Selection Sort và Insertion Sort, Merge Sort là một thuật toán dùng tư tưởng "Chia để trị" (Divide and conquer). Cá nhân mình thấy thuật toán này là một thuật toán dễ hiểu hơn 3 thuật toán sắp xếp cơ bản mình đã đề cập. Ý tưởng của nó như sau:
- Hãy tưởng tượng bạn có một xấp bài lộn xộn, và bạn muốn sắp xếp chúng từ nhỏ đến lớn. Merge Sort hoạt động theo kiểu chia để trị:
- 1. Chia: Cắt xấp bài thành các phần nhỏ hơn, nhỏ đến mức chỉ còn 1 lá bài (mà 1 lá thì đã "sắp xếp" rồi, đúng không?)
  2. Trị: Gộp các phần nhỏ lại với nhau, nhưng khi gộp thì sắp xếp chúng luôn để ra một danh sách đẹp đẽ

## Điểm đặc biệt
- Tính ổn định (Stable)
- Độ phức tạp: Tốt nhất = Trung bình = Xấu nhất = O(n log n)
- Nhược điểm: Tốn thêm bộ nhớ để lưu mảng tạm O(n)
- Không hiệu quả lắm cho danh sách rất nhỏ vì chi phí đệ quy lớn, nhưng phù hợp với danh sách lớn

### Code Python
```python
#Merge Sort - Săp xep tron
#Sap xep tang dan
def merge_sort(lst):
    #Base Case:
    if len(lst) <= 1: #Mang co 0 hoac 1 phan tu thi da sap xep roi
        return lst

    #Chia
    mid = len(lst) // 2
    left = merge_sort(lst[:mid]) #Qua trinh nay duoc lap lai cho den khi chi con 1 phan tu thuoc 1 list rieng biet
    right = merge_sort(lst[mid:])

    return merge(left, right)
def merge(left, right):
    result = []
    i = j = 0

    #So sanh tung cap phan tu va chon nho hon
    while i < len(left) and j < len(right): #Chi chay cho den khi 1 trong 2 list rong, ma i & j la index tu vi tri 0, nen dung < thay vi <=
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    #Gom not phan tu con sot lai neu vong lap dung ma van con phan tu chua xet vi 1 trong 2 list da rong
    result.extend(left[i:]) #Extend(iterable) cho phep mo list ra va them vao tung phan tu mot, chu y rang no khac append
    result.extend(right[j:])

    return result

lst = [4, 2, 7, 1, 3]
print(merge_sort(lst))
```
