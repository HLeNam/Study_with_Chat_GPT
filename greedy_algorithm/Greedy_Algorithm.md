# Thuật Toán Tham Lam (Greedy Algorithm)

## 1. Giới thiệu về thuật toán tham lam
Thuật toán tham lam (Greedy Algorithm) là một phương pháp tối ưu hóa, trong đó tại mỗi bước ta luôn chọn phương án tốt nhất theo tiêu chí cục bộ với hy vọng rằng nó sẽ dẫn đến nghiệm tối ưu toàn cục.

## 2. Điều kiện áp dụng thuật toán tham lam
Không phải bài toán nào cũng có thể giải bằng thuật toán tham lam. Để áp dụng được, bài toán cần thỏa mãn hai tính chất quan trọng:

### 2.1. Tính chất con tối ưu (Optimal Substructure)
Tính chất này yêu cầu rằng nghiệm tối ưu của bài toán lớn có thể được xây dựng từ nghiệm tối ưu của các bài toán con.

#### Cách kiểm tra:
- Chia bài toán thành các bài toán con nhỏ hơn.
- Giải bài toán con một cách độc lập.
- Kiểm tra xem việc ghép nghiệm của các bài toán con có tạo ra nghiệm tối ưu của bài toán lớn hay không.

✅ **Nếu đúng** → Có thể dùng tham lam hoặc quy hoạch động (Dynamic Programming).  
❌ **Nếu sai** → Cần phương pháp khác như quay lui (Backtracking) hoặc quy hoạch động.

#### Ví dụ:
- **Bài toán tìm đường đi ngắn nhất (Dijkstra, Floyd-Warshall)**: Nếu đường đi từ `A → C` ngắn nhất, thì bất kỳ đoạn nào trên đường đó (`A → B`, `B → C`) cũng phải ngắn nhất.

### 2.2. Tính chất lựa chọn tham lam (Greedy Choice Property)
Tính chất này yêu cầu rằng chọn phương án tối ưu cục bộ tại mỗi bước sẽ dẫn đến nghiệm tối ưu toàn cục.

#### Cách kiểm tra:
1. Chọn phương án tham lam trước (phương án tốt nhất tại thời điểm đó).
2. Xem liệu các bước tiếp theo có bị ảnh hưởng không.
3. So sánh với phương pháp khác (như quy hoạch động) để xem có thể đạt được cùng kết quả không.

✅ **Nếu đúng** → Có thể dùng thuật toán tham lam.  
❌ **Nếu sai** → Có thể cần quy hoạch động hoặc quay lui.

#### Ví dụ:
- **Bài toán đổi tiền**: Nếu mệnh giá là `{1, 5, 10, 50}`, thì luôn chọn mệnh giá lớn nhất trước sẽ cho kết quả tối ưu. Nhưng nếu có mệnh giá `{1, 3, 4}` và cần đổi `6`, cách tham lam (`4 + 1 + 1`) không tối ưu bằng (`3 + 3`).

---
## 3. Quy trình kiểm tra xem thuật toán tham lam có áp dụng được không?

| Bước kiểm tra | Ý nghĩa | Nếu KHÔNG đạt được thì sao? |
|--------------|--------|----------------------|
| **Tính chất con tối ưu** | Giải bài toán con giúp giải bài toán lớn | Cần dùng quy hoạch động (Dynamic Programming) |
| **Tính chất lựa chọn tham lam** | Chọn tốt nhất tại mỗi bước dẫn đến nghiệm tối ưu | Tham lam không hoạt động, thử quy hoạch động hoặc quay lui |

✅ **Nếu cả hai tính chất đúng** → Dùng thuật toán tham lam.  
❌ **Nếu ít nhất một tính chất sai** → Xem xét phương pháp khác như Quy hoạch động hoặc Quay lui.

---
## 4. Một số bài toán áp dụng thuật toán tham lam

| Bài toán | Có thể dùng tham lam không? | Giải thích |
|----------------------------|-----------------|-------------|
| **Tìm đường đi ngắn nhất (Dijkstra)** | ✅ Có | Đường đi ngắn nhất có tính chất con tối ưu và lựa chọn tham lam |
| **Bài toán cái túi 0/1 (Knapsack)** | ❌ Không | Cần quy hoạch động để xét hết các khả năng |
| **Bài toán đổi tiền (Coin Change)** | 🔹 Có thể | Phụ thuộc vào mệnh giá tiền |
| **Tạo lịch trình hoạt động (Activity Selection)** | ✅ Có | Chọn hoạt động kết thúc sớm nhất để tối ưu số lượng hoạt động |

---
## 5. Tổng kết
1. **Thuật toán tham lam chọn giải pháp tốt nhất tại mỗi bước** mà không cần xét toàn bộ bài toán.
2. **Chỉ áp dụng được khi bài toán có tính chất con tối ưu và lựa chọn tham lam**.
3. **Nếu không thỏa mãn hai tính chất trên, cần dùng phương pháp khác như quy hoạch động hoặc quay lui**.

🚀 **Trước khi áp dụng thuật toán tham lam, hãy luôn kiểm tra hai tính chất quan trọng!**

