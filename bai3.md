# Báo cáo Bài 3: Cấu hình xác thực SSH và Đẩy dự án lên GitHub



## 1. Nhật ký các lệnh đã thực hiện (Execution Steps)

### Bước 1: Khởi tạo thư mục và Repository cục bộ

```bash
mkdir -p homework/session_04/ex3
cd homework/session_04/ex3
git init

# Cấu hình danh tính local
git config --local user.name "Nguyen Van A"
git config --local user.email "nguyenvana@example.com"
```

### Bước 2: Tạo cặp khóa SSH với thuật toán Ed25519

Sinh cặp khóa SSH Ed25519 bảo mật theo đúng yêu cầu:

```bash
ssh-keygen -t ed25519 -C "nguyenvana@example.com"
```

*(Nhấn Enter để chấp nhận đường dẫn lưu mặc định `~/.ssh/id_ed25519` và thiết lập Passphrase nếu muốn).*

### Bước 3: Đọc và thêm Public Key lên GitHub

Hiển thị nội dung Public Key để sao chép vào cài đặt GitHub (Settings -> SSH and GPG keys -> New SSH key):

```bash
cat ~/.ssh/id_ed25519.pub
```

### Bước 4: Tạo tệp báo cáo và commit ban đầu

```bash
echo "# Bài tập 3: Cấu hình xác thực SSH và Đẩy dự án lên GitHub" > README.md
git add README.md
git commit -m "feat: Initial commit for Exercise 3 SSH setup"
```

### Bước 5: Cấu hình Remote URL (SSH) và Push mã nguồn

```bash
# Đổi tên nhánh mặc định sang main (nếu chưa có)
git branch -M main

# Liên kết repository cục bộ với GitHub bằng URL giao thức SSH
git remote add origin git@github.com:username/repository.git

# Đẩy dữ liệu lên GitHub
git push -u origin main
```

---

## 2. Minh chứng Kết quả Kiểm tra (Verification Outputs)

### A. Kiểm tra kết nối SSH tới GitHub (`ssh -T git@github.com`)

```text
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

### B. Kiểm tra cấu hình Remote URL (`git remote -v`)

```text
origin  git@github.com:username/repository.git (fetch)
origin  git@github.com:username/repository.git (push)
```

---

## 3. Liên kết Repository Remote

* **URL Kho lưu trữ GitHub:** `https://github.com/username/repository`
* **SSH URL:** `git@github.com:username/repository.git`

---

