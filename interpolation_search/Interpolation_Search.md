# Interpolation Search - Tổng hợp kiến thức

## 1. Interpolation Search là gì?

**Interpolation Search** (Tìm kiếm nội suy) là một giải thuật tìm kiếm độc nhất, là phiên bản cải tiến của Binary Search, dùng cho dãy số **đã được sắp xếp** và có phân phối **đồng đều**.

**Tốc độ trung bình:** O(log log n)  
**Tốc độ tối xấu:** O(n) (nếu dữ liệu không đồng đều)

---

## 2. Cách hoạt động

**Công thức tính vị trí: (pos)**

$$
pos = left + \frac{(right - left) \times (key - arr[left])}{arr[right] - arr[left]}
$$

Giống như Binary Search, nhưng thay vì chọn giữa mảng, nội suy sẽ ước lượng vị trí theo tính phân bố.

---

## 3. Thuật toán Interpolation Search

### Python Implementation

```python
def interpolation_search(arr, key):
    left = 0
    right = len(arr) - 1

    while left <= right and key >= arr[left] and key <= arr[right]:
        if arr[left] == arr[right]:
            if arr[left] == key:
                return left
            else:
                return -1

        pos = left + ((right - left) * (key - arr[left])) // (arr[right] - arr[left])

        if arr[pos] == key:
            return pos
        elif arr[pos] < key:
            left = pos + 1
        else:
            right = pos - 1

    return -1

# Ví dụ
arr = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
key = 70
result = interpolation_search(arr, key)
print("Vị trí:", result)
```

---

## 4. Khi nào nên dùng Interpolation Search?

**Nên dùng khi:**

-   Dữ liệu đã sắp xếp.
-   Dữ liệu phân phối đồng đều, không bị lệch.

**Không nên dùng khi:**

-   Dữ liệu không đồng đều (pos estimation sai).
-   Dữ liệu chưa sắp xếp.

---

## 5. So sánh Interpolation Search với Binary Search

| Thuộc tính           | Binary Search    | Interpolation Search |
| -------------------- | ---------------- | -------------------- |
| Cần sắp xếp dữ liệu  | Bắt buộc         | Bắt buộc             |
| Hiệu suất trung bình | O(log n)         | O(log log n)         |
| Trường hợp tối xấu   | O(log n)         | O(n)                 |
| Dữ liệu đồng đều     | Không quan trọng | Cần thiết            |

---

## 6. Bài tập tự luyện có lời giải

### Bài 1: Tìm số

**Input:**

```
10
5 10 15 20 25 30 35 40 45 50
35
```

**Output:**

```
6
```

**Solution:**

```python
def interpolation_search(arr, key):
    left = 0
    right = len(arr) - 1

    while left <= right and key >= arr[left] and key <= arr[right]:
        if arr[left] == arr[right]:
            if arr[left] == key:
                return left
            else:
                return -1

        pos = left + ((right - left) * (key - arr[left])) // (arr[right] - arr[left])

        if arr[pos] == key:
            return pos
        elif arr[pos] < key:
            left = pos + 1
        else:
            right = pos - 1

    return -1

n = int(input())
arr = list(map(int, input().split()))
key = int(input())
print(interpolation_search(arr, key))
```

---

### Bài 2: Tìm vị trí phần tử không tồn tại

**Input:**

```
8
3 6 9 12 15 18 21 24
10
```

**Output:**

```
-1
```

---

### Bài 3: Kiểm tra nhiều phần tử

**Input:**

```
5
2 4 6 8 10
3
4 6 7
```

**Output:**

```
1
2
-1
```

**Solution:**

```python
n = int(input())
arr = list(map(int, input().split()))
m = int(input())
keys = list(map(int, input().split()))

def interpolation_search(arr, key):
    left = 0
    right = len(arr) - 1

    while left <= right and key >= arr[left] and key <= arr[right]:
        if arr[left] == arr[right]:
            if arr[left] == key:
                return left
            else:
                return -1

        pos = left + ((right - left) * (key - arr[left])) // (arr[right] - arr[left])

        if arr[pos] == key:
            return pos
        elif arr[pos] < key:
            left = pos + 1
        else:
            right = pos - 1

    return -1

for key in keys:
    print(interpolation_search(arr, key))
```

---

## 7. Ghi chú

Nếu dữ liệu không phân phối đồng đều, thuật toán có thể rơi vào thời gian O(n), nên cần kiểm tra phân phối dữ liệu trước khi áp dụng.
