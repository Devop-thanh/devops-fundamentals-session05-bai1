# Bài 1: Khôi phục commit đã mất bằng Git Reflog

## 1. Khởi tạo repository

Khởi tạo Git repository bằng lệnh:

```bash
git init
```

Tạo file `feature.txt` với nội dung:

```text
Day la tinh nang quan trong
```

Sau đó thêm file và commit:

```bash
git add .
git commit -m "Them tinh nang quan trong"
```

## 2. Kiểm tra lịch sử commit

Sử dụng lệnh:

```bash
git log --oneline
```

Commit `Them tinh nang quan trong` xuất hiện trong lịch sử.

## 3. Giả lập việc làm mất commit

Thực hiện lệnh:

```bash
git reset --hard HEAD~1
```

Sau khi reset, kiểm tra lại:

```bash
git log --oneline
```

Commit `Them tinh nang quan trong` không còn xuất hiện trong lịch sử hiện tại.

## 4. Tìm lại commit bằng Reflog

Sử dụng lệnh:

```bash
git reflog
```

Kết quả cho thấy commit đã bị mất:

```text
a73092b HEAD@{1}: commit: Them tinh nang quan trong
```

Trong đó `HASH-COMMIT` là mã hash của commit cần khôi phục.

## 5. Khôi phục commit

Sử dụng lệnh:

```bash
git reset --hard HASH-COMMIT
```

Sau khi khôi phục, kiểm tra lại lịch sử:

```bash
git log --oneline
```

Commit `Them tinh nang quan trong` đã xuất hiện trở lại.

## 6. Kiểm tra nội dung file

Sử dụng:

```bash
cat feature.txt
```

Kết quả:

```text
Day la tinh nang quan trong
```

## 7. Kết luận

Đã khôi phục thành công commit bị mất bằng cơ chế Git Reflog sau khi thực hiện `git reset --hard HEAD~1`.

Commit và nội dung file `feature.txt` đã được khôi phục về trạng thái trước khi bị reset.
