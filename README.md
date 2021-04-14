1.	Git là gì?
-	Git là hệ thống quản lý phiên bản phân tán (quản lý được code, lịch sử thay đổi và có khả năng tách nhánh, hỗ trợ tốt cho teamwork, chia task và tổng hợp code dễ dàng hơn)
2.	Cách tạo 1 respository
-	Tạo 1 folder, di chuyển đến folder và gõ lệnh git init
3.	Add & Commit
-	Thêm các thay đổi: git add <tên_tệp_tin> hoặc git add *
-	Commit thay đổi lên HEAD của local respository:
git commit -m “ghi chu”
-	Đẩy các thay đổi lên remote respository:
git push origin master
4.	Branch
-	Tạo nhánh mới:
git branch <tên_nhánh>
-	Chuyển qua làm việc trên nhánh đó:
git checkout <tên_nhánh>
-	Xóa nhánh:
git branch -d <tên_nhánh>
-	Đẩy các thay đổi thông qua nhánh lên remote respository:
git push origin <tên_nhánh>
5.	Git merge & Rebase
-	Khi tạo 1 nhánh mới từ nhánh gốc để thay đổi theo 1 hướng nào đó mà không ảnh hưởng đến nó, khi đó sẽ tạo ra nhiều các commit mới từ nhánh mới này. Sau khi thay đổi đảm bảo hết lỗi, ta có thể tích hợp gộp các commit của nhánh mới với nhánh gốc: 
o	Chuyển về nhánh gốc: git checkout master
o	Sử dụng git merge: git merge <nhánh_mới>
o	Sử dụng git rebase: git rebase <nhánh_mới>
-	Phân biệt git merge & git rebase:
o	Đối với git merge: 
+	Thực hiện bằng cách so sánh giữa điểm rẽ nhánh (commit cơ sở chung giữa các nhánh) và commit cuối của các nhánh cần gộp rồi gộp thành 1 commit tổng hợp (có xử lý xung đột)
+	Các commit sau khi gộp vào vân được sắp xếp theo thời gian của các commit rẽ nhánh 
+	Viết bằng merge thì lưu vết cũng như bảo toàn history của respoitory (ví dụ: xem được commit này từ branch nào,…), tránh việc rewrite lại các thay đổi.
o	Đối với git rebase: 
+	Thực hiện bằng cách lấy tất cả các commit của nhánh mới làm commit cơ sở của nhánh gốc rồi đi sau đó là các commit riêng của nhánh gốc
+	Trong trường hợp xảy ra xung đột giữa điểm tiếp nối commit cơ sở và commit riêng của nhánh gốc thì sẽ xử lý bằng cách viết lại commit riêng đó.
+	Viết bằng rebase thì sẽ có 1 history rõ rang, dễ nhìn, hay còn gọi là linear history, tránh được trường hợp có thêm các merge commit.
6.	Git tag, release
-	Git tag để đánh dấu 1 điểm trong lịch sử commit, thường là các commit đặc biệt, để dễ dàng lấy lại phiên bản cũ hơn
-	Tạo 1 tag mới đánh dấu vào commit: 
git tag -a <tên_tag> -m “ghi chú” <mã hash commit>
(Nếu không gõ mã hash của commit thì mặc định tạo tag cho commit cuối cùng)
-	Xem thông tin về commit được gắn tag:
git show <tên_tag >
-	Đẩy tag lên remote:
o	Với 1 tag: git push origin <tên_tag>
o	Tất cả tag: git push origin –tags
-	Quay về 1 phiên bản bằng tag: thay vì gọi mã hash của phiên bản thì sử dụng tên tag tương ứng: git checkout <tên_tag>
-	Xóa tag:
o	Tại local: git tag -d <tên_tag>
o	Tại remote: git push --delete origin <tên_tag>
-	Khi đã đánh tag cho commit và đẩy lên remote, ta sẽ có phiên bản Releases của commit đó và ta có thể xem lại nội dung các file của commit được đánh tag
7.	Git flow
