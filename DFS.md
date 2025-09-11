#DFS - Depth First Search - Tìm kiếm theo chiều sâu

##DFS là gì?
Hiểu đơn giản như đi khám phá mê cung: Hãy tưởng tượng bạn đang trong một mê cung với nhiều ngã rẽ. Mỗi ngã ré dẫn đến 1 phòng mới, và mỗi phòng lại có thêm các ngã rẽ khác. DFS giống như cách bạn khám phá mê cung này theo kiểu: đi thật sâu vào 1 con đường cho đến khi không đi được nữa, rồi quay lại thử con đường khác.
Ý tưởng chính của DFS:
- Bắt đầu từ một điểm (gọi là nút), bạn khám phá hết tất cả các con đường đi từ điểm đó, nhưng thay vì đi hết mọi ngã rẽ cùng một lúc, bạn chọn một ngã rẽ và đi thật sâu vào đó trước. Nếu gặp ngõ cụt, bạn quay lại ngã rẽ gần nhất và thử ngã rẽ khác.
- Để tránh vòng vòng (vì mê cung có thể có đường nối lại), bạn đánh dấu những nơi đã đi qua

###VD minh họa:
Code Python: Mê cung đơn giản
- DFS (đệ quy):
```python
def dfs_recursive(u, graph, visited):
    if u in visited:
        return
    visited.add(u)
    print(u, end = ' ')
    for v in graph[u]:
        dfs_recursive(v, graph, visited)
```
####Ứng dụng thuật toán này trong bài toán Count Island - Đếm "hòn đảo" 1 trong ma trận nhị phân
Ý tưởng chính để làm bài toán này là ta sẽ sử dụng DFS, đánh dấu bằng việc mỗi lần quét qua ô 1 thì sẽ đánh dấu thành 0 để không bị đếm lại, sau đây là code Python cho bài toán này:
```python
#Count Island 1 - Dem hon dao 1 trong ma tran
#Cho ma tran nhi phan gom n hang & m cot chi bao gom so 0 va 1. Hay dem so luong mien cac so 1 trong ma tran, cac o so 1 duoc coi la cung mien neu chung co chung canh
import sys
#Khai bao bien toan cuc (vi trong ham def co can, nhung ham main ms khai bao)
n, m = 0, 0
a = []
path = [[-1, 0], [0, -1], [1, 0], [0, 1]] #Di chuyen 4 huong xung quanh
#Ki thuat DFS - Depth First Search - Tim kiem theo chieu sau
def loang(i, j):
    a[i][j] = 0
    for x, y in path:
        i1 = i + x
        j1 = j + y
        if i1 >= 0 and i1 <n and j1 >= 0 and j1 < m and a[i1][j1] == 1: # < n & < m vi index chay tu 0
            loang(i1, j1) #de quy (*)
if __name__ == '__main__':
    n, m = map(int, input().split())
    #Nhap vao 1 list
    for row in range(n):
        b = list(map(int, input().split()))
        if len(b) != m:
            sys.exit()
        a.append(b)
    dem = 0
    for i in range(n):
        for j in range(m):
            #mỗi lần gặp 1, gọi DFS để "loang" hết vùng → đếm được số đảo.
            if a[i][j] == 1:
                dem += 1
                loang(i, j) #Vi trong def loang co ham de quy, no se kiem tra het tat ca o 1 xung quanh,roi gan 0, nen vong lap moi o day no se ko check nua
```
- (*) Nhờ có cơ chế đệ quy (recursive stack) nên mỗi lần chạy ô nào thì nó sẽ lưu vào stack, nên sau khi hàm con chạy xong, chương trình sẽ pop stack, và quay lại đúng chỗ gần nhất mà nó đã tạm dừng (hàm cha) và tiếp tục chạy lệnh còn lại.
----------------------
Input:
4 5
1 1 0 0 0
1 1 0 0 1
0 0 0 1 1
0 0 0 0 0

Output:
2
----------------------
