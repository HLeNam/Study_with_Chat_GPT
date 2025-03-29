# Sliding Window - Tổng hợp kiến thức

## 1. Sliding Window là gì?

**Sliding Window** là kỹ thuật tối ưu dùng cho các bài toán liên quan đến:

-   **Dãy con liên tiếp** (subarray, substring)
-   Cần kiểm tra tổng, độ dài, tần suất... của dãy con.

**Ý tưởng:** Duy trì một "cửa sổ" liên tiếp trong dãy và di chuyển nó để thoả mãn điều kiện bài toán.

Cửa sổ có 2 cách triển khai:

-   **Fixed size window:** Kích thước cố định.
-   **Dynamic size window:** Kích thước thay đổi linh hoạt.

---

## 2. Cách triển khai

### Dynamic Size Window (phổ biến nhất)

**Bước 1:** Dùng 2 biến `l` và `r` (cận trái và phải của cửa sổ).

**Bước 2:** Duy trì một biến `current_sum` (hoặc điều kiện cần kiểm tra).

**Bước 3:**

-   Mỗi bước, mở rộng `r` sang phải.
-   Nếu điều kiện vi phạm, thu hẹp `l` sang phải.

---

## 3. Ví dụ cơ bản

### Bài toán:

Tìm dãy con liên tiếp đầu tiên có tổng bằng `s`.

### Input:

```
7
1 3 2 5 1 1 2
8
```

### Solution:

```python
n = int(input())
a = list(map(int, input().split()))
s = int(input())

l = 0
current_sum = 0
found = False

for r in range(n):
    current_sum += a[r]

    while current_sum > s and l <= r:
        current_sum -= a[l]
        l += 1

    if current_sum == s:
        print(*a[l:r+1])
        found = True
        break

if not found:
    print(-1)
```

**Giải thích:**

-   Duy trì tổng `current_sum` từ l → r.
-   Nếu tổng vượt quá s, dịch `l` sang phải.
-   Nếu tổng = s → in ra dãy con.

---

## 4. Bài toán nâng cao

### Đề:

Tìm độ dài lớn nhất của đoạn liên tiếp có tổng ≤ s.

### Solution:

```python
n = int(input())
a = list(map(int, input().split()))
s = int(input())

l = 0
current_sum = 0
max_len = 0

for r in range(n):
    current_sum += a[r]

    while current_sum > s and l <= r:
        current_sum -= a[l]
        l += 1

    max_len = max(max_len, r - l + 1)

print(max_len)
```

---

## 5. Khi nào nhận biết dùng Sliding Window?

Hãy chú ý khi đề có những từ khoá:

-   **Dãy con liên tiếp**
-   Tìm tổng, độ dài, số lượng ký tự, điều kiện liên tiếp...
-   Tìm đoạn đầu tiên, đoạn ngắn nhất, dài nhất...

90% trường hợp → Sliding Window chính là chìa khoá.

---

## 6. Bài tập tự luyện

### Dễ

1. Tìm đoạn liên tiếp đầu tiên có tổng đúng bằng `s`.
2. Tìm độ dài đoạn liên tiếp dài nhất có tổng ≤ `s`.

### Trung bình

3. Tìm đoạn liên tiếp có tổng lớn nhất.
4. Đếm số đoạn liên tiếp có tổng đúng bằng `s`.

### Khó

5. Tìm đoạn liên tiếp ngắn nhất có tổng ≥ `s`.
6. Cho dãy chỉ gồm 0 và 1, tìm độ dài lớn nhất của đoạn liên tiếp chỉ chứa 1, cho phép đổi tối đa `k` số 0 thành 1.

---

## 7. Kinh nghiệm

**Nếu bạn có tư duy duyệt chậm O(n^2), Sliding Window sẽ giảm xuống còn O(n).**

> Hãy luyện tập nhiều bài với Sliding Window, bạn sẽ thấy nó mạnh thế nào!

---
