# Thuật toán sắp xếp nổi bọt - Bubble Sort
Bubble Sort là thuật toán sắp xếp đơn giản, hoạt động bằng cách:
- Đi từ trái sang phải, so sánh từng cặp phần tử liền kề
- Đổi chỗ nếu chúng sai thứ tự
- Sau mỗi lượt pass, phần tử lớn nhất còn lại sẽ "nổi" về cuối dãy
- Lặp lại các lượt pass, nhưng mỗi lần có thể bỏ qua phần đuôi đã đúng chỗ

##Vì sao ý tưởng trên lại đúng?
Dựa vào tính bất biến - invariant, sau lần pass thứ k, k phần tử lớn nhất đã nằm đúng ở k vị trí cuối cùng của mảng

### Độ phức tạp & Tính chất
- Thời gian: O(n^2) (trung bình, xấu nhất)
             O(n) (tốt nhất, nếu có "early stop")
- Bộ nhớ: O(1) (in-place)
- Tính ổn định (Stable): Nếu chỉ đổi khi a[j] > a[j + 1] (không dùng >=) thì thứ tự của phần tử bằng nhau được giữ nguyên theo thứ tự xuất hiện của chúng

#### Code Python: Sắp xếp tăng dần
def bubble_sort_tang(lst):
    n = len(lst)
    for i in range(n - 1):
        swapped = False
        for j in range(n - i - 1):
            if lst[j] > lst[j + 1]: #Đổi dấu nếu muốn sắp xếp giảm dần
                lst[j], lst[j + 1] = lst[j + 1], lst[j]
                swapped = True
                #Neu muon in ra chi tiet cua cac pass thi print(lst) o day
        print(lst) #In ra sau cac pass
        if not swapped: #Neu sau pass nay ko doi cho, swapped van la False thi mang nay k can sap xep
            break #Thoat vong lap i ma khong can phai kiem tra cac pass tiep theo
    return lst
if __name__ == '__main__':
    l = list(map(int, input().split()))
    print(bubble_sort_tang(l))

##### Vào ngày đầu tiên tôi học thuật toán này ở trường từ một đàn anh dạy C++, code đó không tối ưu được như trên, và có độ phức tạp là O(n^2), vậy điều gì đã xảy ra?
- Vòng for i được duyệt từ 0 -> n, vòng for j được duyệt từ 0 đến n - 1, không sai, nhưng điều đó khiến lặp so sánh ngay cả khi mảng đã sắp xếp xong
- Không có 'early stop' để kết thúc vòng lặp sớm
  --> Dẫn đến tổng so sánh: (n - 1) + (n - 2) + ... + 1 = (n*(n - 1)) / 2 thay vì n - 1 lần
