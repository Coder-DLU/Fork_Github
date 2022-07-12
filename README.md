# Fork_Github
Quá trình làm việc với các nhánh của git và sử dụng Frok để hỗ trợ hiển thị lịch sử commit một cách trực quan hơn.
# 1: Cài đặt và cấu hình git
# Kiểm tra phiên bản GIT
git --version
# Danh sách các thiết lập cấu hình
git config --list
# Thiết lập tên
git config --global user.name "Tên của Bạn"
# Thiết lập email
git config --global user.email emailcuaban@domain.com
# Tạo kho chứa mới :
git init
# sao chép một kho chứa về local:
git clone
#Khi bạn cần tạo ra một Repo Git mà nó chỉ có chức năng lưu trữ - không có thư mục làm việc thì thực hiện lệnh:
git init --bare
#Bạn có thể thực hiện lệnh git add nhiều lần để tạo tạo ra một snapshot cuối cùng trước khi thực hiện commit.
git add
#Trường hợp dùng phổ biến là đưa toàn bộ thư mục làm việc vào giám sát, và tạo snapshot trong vùng staging cho chúng thì dùng cú pháp lệnh:
git add --all
# Hoặc
git add -A
# Hoặc add [thư mục hiện tại]
git add .
# Lệnh git status hiện thị thông tin khác nhau (do thêm mới, xóa đi, sửa đổi các file) giữa các file
git status
#Lệnh commit cơ bản, đơn giản nhất là thực hiện với tham số -m để kèm dòng thông tin về commit
git commit -m "Ghi chú về commit"
#Khi cho tham số -a thì nó tương đương thực hiện lệnh git add để đưa các file đang được giám sát có sự thay đổi vào staging rồi tự động chạy git commit
git commit -a -m "Ghi chú về commit"
#Nếu commit đã được tạo ra nhưng chưa thực hiện push lên remote (khi có làm việc với Remote Repo - nói ở các phần sau) thì bạn có thể tạo ra commit mới thay thế cho commit cuối cùng đó. Dùng trong trường hợp không muốn tạo ra nhiều commit trong lịch sử commit thì cho vào lệnh tham số --amend
git commit --amend -m "Thông tin về commit"
# Khi đã thực hiện commit, commit đó chưa public (chưa đẩy lên Remote Repo bằng lệnh git push) thì bạn có thể hủy (undo) commit đó với hai trường hợp bằng lệnh git reset như sau:
git reset với tham số --soft
#Trường hợp này sẽ hủy commit cuối, con trỏ HEAD sẽ chuyển về commit cha. Đồng thời những thay đổi của commit cuối được chuyển vào vùng staging nhằm để có cơ hội commit lại hoặc sửa đổi, cú pháp lệnh như sau:
git reset --soft HEAD~1
#Khi dùng tham số --hard thì kết quả giống với dùng tham số --soft, chỉ có một khác biết là nội dung thay đổi của commit cuối không đưa đưa vào staging mà bị hủy luôn. Trường hợp này dùng khi bạn quyết định hủy hoàn toàn commit cuối
git reset --hard HEAD~1
# Mặc đinh thi hành git log nó liệt kê các commit theo thứ tự từ mới nhất đến cũ nhất, mỗi commit có các thông tin gồm: mã hash của commit, dòng thông báo, người tạo commit và ngày tạo commit
git log
Một số phím chức năng bạn có thể nhập đề điều hướng và tìm kiếm trong log như:
return - dòng tiếp theo
w - trang tiếp
spacebar - trang trước
q - thoát
?pattern - tìm kiếm, với pattern là mẫu tìm kiếm (keyword)
/pattern - giống ?pattern
n - đến vị trí tìm kiếm phía dưới
N - đến kết quả tìm kiếm phía trước
#Lệnh git diff hiện thị thông tin thay đổi giữa thư mục làm việc và vùng index (staging) hoặc với commit cũ, thông tin thay đổi giữa index(staging) và commit, thông tin thay đổi giữa hai nhánh ...
git diff
Khi có sự thay đổi của thư mục làm việc mà chưa chỉ mục, thì có thể xem sự thay đổi của nó với commit cuối
git diff
Kiểm tra sự thay đổi của index (staging) với commit cuối
git diff --staged
Kiểm tra thay đổi giữa hai commit
git diff hash-commit1 hash-commit2
Kiểm tra sự thay đổi của hai nhánh
git diff branch1 branch2
#Trên máy của bạn có một Git Repo ở đường dẫn path-git, bạn có thể copy sang vị trí khác bằng lệnh:
git clone path-git
#Giả sử đang ở nhánh nào đó, muốn chuyển sang nhánh master thì thực hiện lệnh:
git checkout master
Giả sử có file index.html, muốn phục hồi nó về phiên bản ở commit có mã hash là HASH, thì thực hiện:

git checkout HASH index.html
Nếu bạn muốn phục hồi nội dung từ index (staging nếu có, nếu không từ commit cuối) thì đơn giản là

git checkout index.html
Phục hồi nhiều file, ví dụ *.html từ index (staging nếu có, nếu không từ commit cuối)

git checkout -- *.html
Có thể thực hiện với tất cả các file bằng

git checkout -- .
Khi bạn trở về hẳn một commit có mã HASH nào đó bằng lệnh:

git checkout HASH
Thì lúc này con trỏ HEAD sẽ chuyển đến commit này, và Git ở chế độ head detached, bạn làm việc trên một nhánh tạm thời

Nếu có thực hiện các commit trên nhánh này và cần lưu lại thì cuối cùng tạo nhánh mới bằng lệnh

git switch -c ten-nhanh-moi
https://xuanthulab.net/lam-viec-voi-nhanh-branch-tao-nhanh-gop-nhanh-trong-git.html
