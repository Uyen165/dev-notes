# Merge Sort - Thuật toán sắp xếp trộn
Thuộc nhóm Thuật toán nhanh hơn và mang tính thực tế hơn 3 thuật toán Bubble Sort, Selection Sort và Insertion Sort, Merge Sort là một thuật toán dùng tư tưởng "Chia để trị" (Divide and conquer). Cá nhân mình thấy thuật toán này là một thuật toán dễ hiểu hơn hẳn 3 thuật toán sắp xếp cơ bản mình đã để cập. Ý tưởng của nó như sau:
- Hãy tưởng tượng bạn có một xấp bài lộn xộn, và bạn muốn sắp xếp chúng từ nhỏ đến lớn. Merge Sort hoạt động theo kiểu chia để trị:
- 1. Chia: Cắt xấp bài thành các phần nhỏ hơn, nhỏ đến mức chỉ còn 1 lá bài (mà 1 lá thì đã "sắp xếp" rồi, đúng không?)
  2. Trị: Gộp các phần nhỏ lại với nhau, nhưng khi gộp thì sắp xếp chúng luôn để ra một danh sách đẹp đẽ

## Điểm đặc biệt
- Tính ổn định (Stable)
- Độ phức tạp: Tốt nhất = Trung bình = Xấu nhất = O(n log n)
- Nhược điểm: Tốn thêm bộ nhớ để lưu mảng tạm O(n)
- Không hiệu quả lắm cho danh sách rất nhỏ vì chi phí đệ quy lớn, nhưng phù hợp với danh sách lớn

### Code Python
