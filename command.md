# Tài liệu chi tiết các lệnh Git

Tài liệu này cung cấp giải thích và ví dụ về các lệnh Git cơ bản, giúp bạn dễ dàng hiểu và áp dụng.

---

## 1. Cài đặt & Khởi tạo (SETUP & INIT)

Hướng dẫn thiết lập thông tin người dùng và khởi tạo kho lưu trữ Git mới.

- **Thiết lập tên người dùng:**
  ```bash
  git config --global user.name "[firstname lastname]"
  ```
  > Đây là cách bạn được nhận dạng khi xem lại lịch sử phiên bản. [cite: 1]

- **Thiết lập email:**
  ```bash
  git config --global user.email "[valid-email]"
  ```
  > Đặt địa chỉ email liên kết với mỗi commit. [cite: 1]

- **Bật màu sắc dòng lệnh:**
  ```bash
  git config --global color.ui auto
  ```
  > Tự động thêm màu sắc vào đầu ra của dòng lệnh Git, giúp dễ dàng theo dõi và xem lại. [cite: 1]

- **Khởi tạo kho lưu trữ Git:**
  ```bash
  git init
  ```
  > Biến một thư mục hiện có thành kho lưu trữ Git. [cite: 1]

- **Sao chép kho lưu trữ từ xa:**
  ```bash
  git clone [url]
  ```
  > Tải xuống toàn bộ kho lưu trữ Git từ máy chủ về máy tính cục bộ. [cite: 1, 2]

---

## 2. Giai đoạn & Ảnh chụp nhanh (STAGE & SNAPSHOT)

Quản lý các tệp đã thay đổi và tạo "snapshot" lịch sử.

- **Kiểm tra trạng thái:**
  ```bash
  git status
  ```
  > Hiển thị trạng thái kho lưu trữ, các tệp đã thay đổi, đã dàn dựng, chưa theo dõi. [cite: 2]

- **Thêm tệp vào staging:**
  ```bash
  git add [file]
  ```
  > Thêm tệp đã thay đổi vào khu vực dàn dựng. [cite: 2]
  - *Ví dụ:* `git add index.html`

- **Bỏ tệp khỏi staging:**
  ```bash
  git reset [file]
  ```
  > Bỏ tệp ra khỏi khu vực dàn dựng, giữ thay đổi trong thư mục làm việc. [cite: 2]

- **So sánh thay đổi với staging:**
  ```bash
  git diff
  ```
  > So sánh thay đổi trong thư mục làm việc với phiên bản đã dàn dựng. [cite: 3]

- **So sánh thay đổi đã staging với commit cuối:**
  ```bash
  git diff --staged
  ```
  > So sánh thay đổi đã ở trong staging với commit cuối cùng. [cite: 3]

- **Tạo commit mới:**
  ```bash
  git commit -m "[descriptive message]"
  ```
  > Lưu nội dung đã dàn dựng thành commit mới. [cite: 3]
  - *Ví dụ:* `git commit -m "Thêm nút đăng nhập vào trang chủ"`

---

## 3. Nhánh & Hợp nhất (BRANCH & MERGE)

Cách làm việc với nhánh để cô lập và tích hợp thay đổi.

- **Liệt kê nhánh:**
  ```bash
  git branch
  ```
  > Liệt kê tất cả nhánh, nhánh hiện tại có dấu `*`. [cite: 4]

- **Tạo nhánh mới:**
  ```bash
  git branch [branch-name]
  ```
  > Tạo nhánh mới từ commit hiện tại. [cite: 4]
  - *Ví dụ:* `git branch new-feature`

- **Chuyển nhánh:**
  ```bash
  git checkout [branch]
  ```
  > Chuyển sang nhánh khác, cập nhật thư mục làm việc. [cite: 4]
  - *Ví dụ:* `git checkout new-feature`

- **Hợp nhất nhánh:**
  ```bash
  git merge [branch]
  ```
  > Hợp nhất lịch sử nhánh chỉ định vào nhánh hiện tại. [cite: 4]
  - *Ví dụ:* Khi ở nhánh `main`, chạy `git merge new-feature` để hợp nhất thay đổi từ `new-feature` vào `main`.

- **Xem lịch sử commit:**
  ```bash
  git log
  ```
  > Hiển thị lịch sử commit của nhánh hiện tại. [cite: 4]

---

## 4. Kiểm tra & So sánh (INSPECT & COMPARE)

Xem lại lịch sử và so sánh các phiên bản tệp hoặc nhánh.

- **Lịch sử commit chi tiết:**
  ```bash
  git log
  ```
  > Hiển thị lịch sử commit chi tiết. [cite: 5]

- **Lịch sử commit giữa hai nhánh:**
  ```bash
  git log branchB..branchA
  ```
  > Hiển thị commit chỉ có trên `branchA` mà không có trên `branchB`. [cite: 5]

- **Lịch sử commit của một tệp (kể cả đổi tên):**
  ```bash
  git log --follow [file]
  ```
  > Hiển thị lịch sử commit đã thay đổi tệp, kể cả khi đổi tên. [cite: 5]

- **So sánh nội dung giữa hai nhánh:**
  ```bash
  git diff branchB...branchA
  ```
  > Hiển thị sự khác biệt của nội dung giữa hai nhánh. [cite: 5]

- **Hiển thị thông tin chi tiết một đối tượng Git:**
  ```bash
  git show [SHA]
  ```
  > Hiển thị thông tin chi tiết commit hoặc tệp. [cite: 5]

---

## 5. Theo dõi thay đổi đường dẫn (TRACKING PATH CHANGES)

Quản lý việc xóa tệp và thay đổi đường dẫn.

- **Xóa tệp khỏi dự án:**
  ```bash
  git rm [file]
  ```
  > Xóa tệp và dàn dựng hành động này để commit. [cite: 6]

- **Đổi tên hoặc di chuyển tệp:**
  ```bash
  git mv [existing-path] [new-path]
  ```
  > Đổi tên/di chuyển tệp và tự động dàn dựng thay đổi. [cite: 6]

- **Hiển thị log commit kèm thống kê di chuyển tệp:**
  ```bash
  git log --stat -M
  ```
  > Hiển thị log commit với thống kê và chỉ báo di chuyển đường dẫn. [cite: 6]

---

## 6. Bỏ qua các mẫu (IGNORING PATTERNS)

Ngăn Git theo dõi các tệp không cần thiết.

- **Thiết lập tệp bỏ qua toàn hệ thống:**
  ```bash
  git config --global core.excludesfile [file]
  ```
  > Hữu ích cho các tệp muốn Git bỏ qua trên tất cả kho lưu trữ cục bộ, ví dụ tệp cài đặt trình soạn thảo. [cite: 6]

- **Bỏ qua tệp cho từng dự án:**
  - Tạo tệp `.gitignore` trong thư mục gốc kho lưu trữ.

---

## 7. Chia sẻ & Cập nhật (SHARE & UPDATE)

Tương tác với kho lưu trữ từ xa để cộng tác.

- **Thêm kho lưu trữ từ xa:**
  ```bash
  git remote add [alias] [url]
  ```
  > Thêm kho lưu trữ từ xa với bí danh. [cite: 7]
  - *Ví dụ:* `git remote add origin https://github.com/user/repo.git`

- **Tải về nhánh/commit mới từ remote:**
  ```bash
  git fetch [alias]
  ```
  > Tải về tất cả nhánh và commit mới từ remote. [cite: 7]

- **Hợp nhất nhánh từ xa vào nhánh hiện tại:**
  ```bash
  git merge [alias]/[branch]
  ```
  > Hợp nhất nhánh từ xa đã fetch vào nhánh hiện tại. [cite: 7]

- **Đẩy commit lên remote:**
  ```bash
  git push [alias] [branch]
  ```
  > Đẩy commit từ nhánh cục bộ lên remote. [cite: 7]
  - *Ví dụ:* `git push origin main`

- **Lấy và hợp nhất commit mới từ remote:**
  ```bash
  git pull
  ```
  > Lấy và hợp nhất commit mới từ remote vào nhánh hiện tại. [cite: 7]

---

## 8. Viết lại lịch sử (REWRITE HISTORY)

Thay đổi lịch sử commit. **Cẩn thận khi dùng trên commit đã chia sẻ!**

- **Di chuyển chuỗi commit của nhánh hiện tại:**
  ```bash
  git rebase [branch]
  ```
  > Tạo lịch sử tuyến tính, sạch sẽ hơn. [cite: 8]

- **Đặt lại thư mục làm việc và staging về trạng thái commit cụ thể:**
  ```bash
  git reset --hard [commit]
  ```
  > Xóa vĩnh viễn các thay đổi chưa commit. [cite: 8]

---

## 9. Commit tạm thời (TEMPORARY COMMITS)

Lưu trữ tạm thời các thay đổi chưa sẵn sàng để commit.

- **Lưu trữ thay đổi chưa commit:**
  ```bash
  git stash
  ```
  > Lưu thay đổi chưa commit và chưa dàn dựng, làm sạch thư mục làm việc. [cite: 8]

- **Hiển thị danh sách stash:**
  ```bash
  git stash list
  ```
  > Hiển thị danh sách các stash đã lưu. [cite: 8]

- **Áp dụng lại thay đổi từ stash gần nhất:**
  ```bash
  git stash pop
  ```
  > Áp dụng lại thay đổi từ stash gần nhất và xóa nó khỏi danh sách. [cite: 8]

- **Xóa stash gần nhất:**
  ```bash
  git stash drop
  ```
  > Xóa stash gần nhất khỏi danh sách. [cite: 8]

---