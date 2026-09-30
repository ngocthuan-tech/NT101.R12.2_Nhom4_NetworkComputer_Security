# Task 2.3 - Automatic Mono-alphabetic Substitution Cipher Cracker

## 1. Mục tiêu

Xây dựng chương trình hỗ trợ tự động giải mã **Mono-alphabetic Substitution Cipher** khi chỉ biết ciphertext và không biết trước khóa.

Chương trình hỗ trợ:
- Nhập ciphertext trực tiếp từ bàn phím.
- Đọc ciphertext từ file.
- Tự động tìm khóa giải mã có khả năng đúng cao.
- Đánh giá plaintext dựa trên đặc trưng thống kê của tiếng Anh.
- Hiển thị khóa, plaintext tốt nhất và một số thông tin về quá trình tìm kiếm.

## 2. Phương pháp

Do Mono-alphabetic Substitution Cipher có không gian khóa rất lớn (`26!`), chương trình không thể thử toàn bộ các khóa.

Chương trình sử dụng phương pháp tìm kiếm heuristic:

1. Chuẩn hóa ciphertext.
2. Khởi tạo một substitution key.
3. Giải mã ciphertext bằng key hiện tại.
4. Đánh giá plaintext bằng mô hình thống kê N-gram của tiếng Anh.
5. Sinh key mới bằng cách hoán đổi hai ký tự trong key.
6. Sử dụng Hill Climbing để giữ lại các key tạo ra plaintext có điểm số tốt hơn.
7. Thực hiện nhiều lần tìm kiếm với các key khởi tạo khác nhau (Random Restart).
8. Chọn key và plaintext có điểm số tốt nhất.

Quy trình tổng quát:

Ciphertext
    ↓
Preprocessing
    ↓
Generate Initial Key
    ↓
Decrypt
    ↓
N-gram Scoring
    ↓
Hill Climbing
    ↓
Random Restart
    ↓
Best Key + Best Plaintext

## 3. Cấu trúc thư mục

```text
Task_2_3/
├── main.py
├── substitution.py
├── scorer.py
├── README.md
└── data/
    ├── ciphertext.txt
    └── english_quadgrams.txt