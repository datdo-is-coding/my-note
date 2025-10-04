KIẾN THỨC CẦN THIẾT ĐỂ HỌC GIT

Đa số thời gian ta sẽ tương tác với Command Prompt hoặc PowerShell với Windows và Terminal đối với Linux. Cần biết sử dụng lệnh tương tác với cửa sổ command line (CLI) : pwd,cd,mkdir,ls,... là **y****êu cầu tối thiểu.**

PHẦN MỀM CẦN THIẾT:

- IDE: vscode
- Git ( tải từ trang chính chủ của git) lưu ý nhớ thêm git vào path để có thể sử dụng lệnh git trong CMD và PowerShellS
- Cài extension git graph trong vscodevscode

**PHẦN 1: GIỚI THIỆU HỆ THỐNG QUẢN LÝ PHIÊN BẢN VÀ GIT**

**Khái niệm Version Control System**

Là hệ thống theo dõi và lưu lại các thay đổi của tập tin theo thời gian. VCS giúp ghi lại ai thực hiện thay đổi, thay đổi gì và khi nào

**Lợi ích**

- khôi phục phiên bản cũ khi có lỗi
- so sánh sự khác biệt giữa các phiên bản
- biết rõ ai thay đổi, thay đổi gì và khi nào
- bảo vệ dữ liệu và hỗ trợ làm việc nhóm

**Các loại VCS :**

- _Centralized VCS_ (có một máy chủ trung tâm và có rủi ro khi server hỏng)
- _Distributed VCS_(như GIT, Mercurial, mỗi người có một bản sao và linh hoạt hơn).

**Nguyên lý hoạt động của GIT**

1) Snapshot thay vì Diff: Git lưu bản chụp của toàn bộ hệ thống

2) Toàn vẹn dữ liệu với SHA-1: bảo vệ dữ liệu bằng mã định danh 40 ký tự

3) Nguyên lý "Offline-first": cấc thao tác commit, tạo nhánh, gộp nhánh không cần mạng. Chỉ khi cần chia sẻ code (push/pull), bạn mới cần Internet

**CÀI ĐẶT VÀ CẤU HÌNH GIT**
Cài đặt Git
- LINUX: _sudo apt install git_
- Windows: cài từ nguồn
Cấu hình cơ bản
- git config —global user.name "name"
- git config —global user.email "@mail.com"
- git config —global core.editor "code —wait"

**PHẦN 2: QUY TRÌNH LÀM VIỆC GIT CƠ BẢN**

a) **Khởi tạo và sao chép kho (REPOSITORY)**

Khởi tạo repository mới: để bắt đầu dùng Git cho dự án mới, tạo repository trong thư mục dự án. Lệnh git init sẽ tạo thư mục ẩn .git/ để git lưu trữ dữ liệu và theo dõi dự án

![](https://beta.appflowy.cloud/api/file_storage/ff47d52f-3fb3-44ec-95fe-a0a2f689b195/v1/blob/b17a92cf%2D01e4%2D4777%2D9df2%2D6c6bb1f5a8d4/NBEXu4ZIwnruwTl59nwykLxKppDsO4F_o7IhYENJnxw=.png)

Sao chép repo từ xa: để làm việc với dự án có sẵn, cần sao chép (clone) repo từ máy chủ về máy tính. Lệnh git clone sẽ tải về toàn bộ lịch sử và các nhánh của dự án

![](https://beta.appflowy.cloud/api/file_storage/ff47d52f-3fb3-44ec-95fe-a0a2f689b195/v1/blob/b17a92cf%2D01e4%2D4777%2D9df2%2D6c6bb1f5a8d4/tW3JyYLxCvtLDqfxj9HbpqW698GweKQvHi2CibB3PWU=.png)

Khi clone, Git tạo một thư mục mới với tên giống với tên repo. Có thể đặt tên thư mục khác như sau:

![](https://beta.appflowy.cloud/api/file_storage/ff47d52f-3fb3-44ec-95fe-a0a2f689b195/v1/blob/b17a92cf%2D01e4%2D4777%2D9df2%2D6c6bb1f5a8d4/DIOY5uqUaQMPk98285M204nI9JX5VdvA9O-c31eYWpI=.png)  

Windows: \r \n (CARRIAGE RETURN) (LINE FEED)

Linux: \n (LINE FEED)

Windows và Linux xử lý xuống dòng khác nhau nên ta congfigure core.autocrlf

git config —global core.autocrlf true (WINDOWS MACHINE)

git config —global core.autocrlf input (LINUX MACHINE)

Cấu hình editor (IDE):

git config —global core.editor "code —wait"

  

**b) QUY TRÌNH LÀM VIÊC CỦA GIT**

WORKING DIR → git add → STAGING AREA → git commit → REPO→git push→ GITHUB

git add : đưa file vào giao đoạn staging( khi dùngg "git add . " : thêm tất cả các file)

git commit -m "add file one" : khi commit sẽ đưa vào repo và khi commit luôn luôn có comment

![](https://beta.appflowy.cloud/api/file_storage/ff47d52f-3fb3-44ec-95fe-a0a2f689b195/v1/blob/b17a92cf%2D01e4%2D4777%2D9df2%2D6c6bb1f5a8d4/BxSNc08j_C9iA001AM-YCBvEz2-EsJZPBLgnPfKkLNI=.png)![](https://beta.appflowy.cloud/api/file_storage/ff47d52f-3fb3-44ec-95fe-a0a2f689b195/v1/blob/b17a92cf%2D01e4%2D4777%2D9df2%2D6c6bb1f5a8d4/RgW7D0voLhAL3-RpitH-QBYTZm17WFZ8RQj1ogvcnpY=.png)

"git log " : trả về lịch sử (log)

"git log —oneline" : trả về lịch sử trong đúng 1 dòng

  

**L****ƯU** **Ý:** khi commit thay đổi, thay đổi chỉ nên tập trung vào 1 tính năng.

  

.gitignore : sử dụng khi không muốn git lưu trữ những file này (ví dụ như API key,Node module).

.gitconfig: cd về root dir ( chuyển về thư mục root) ⇒ cat .gitconfig :đọc file config

  

Nguyên lý hoạt động của **commit****:**

Hoạt động như một node. Commit đầu tiên có parent chỉ đến NULL. Mỗi node có một mã hash riêng biệt và parent chỉ về địa chỉ hash của node trước đó. Giải thích cho nguyên lý tại sao ta có thể quay về thay đổi cũ .

Info lưu thông tin như người thay đổi (username), email , thời gian thay đổi.

![](https://beta.appflowy.cloud/api/file_storage/ff47d52f-3fb3-44ec-95fe-a0a2f689b195/v1/blob/b17a92cf%2D01e4%2D4777%2D9df2%2D6c6bb1f5a8d4/ttZiUKv1PNQi7f8f-4snS_Ulupy6cvL0kEN2sk79YA4=.png)  

3. **Các nhánh (branch) trong GIT**

Tại sao lại có các nhánh trong GIT, các nhánh phục vụ cho việc tách dự án ra nhiều nhánh. Ví dụ khi phát triển 1 ứng dụng, người này cần làm thanh tìm kiếm còn người khác làm thanh phần khác, ta tách dự án ra nhiều nhánh và cuối cùng ta ghép các nhánh lại để tạo thành 1 dự án duy nhất. Ý nghĩa của việc này giúp ta dễ theo dõi dự án và dễ sửa lỗi

**a) Tạo nhánh trong git**

![](https://beta.appflowy.cloud/api/file_storage/ff47d52f-3fb3-44ec-95fe-a0a2f689b195/v1/blob/b17a92cf%2D01e4%2D4777%2D9df2%2D6c6bb1f5a8d4/nbAoa2MBjUPesyU4QIavyDikEdSs31MB4YQFuNP8alE=.png)

"git branch ": trả về các nhánh (branch) đang có

"git branh name-of-branch" : tạo 1 nhánh mới với tên

"git switch name-of-branch": di chuyển đến nhánh sẵn có

"git checkout name-of-branch": di chuyển đến nhánh sẵn có

SHORTCUT

"git switch -c dark-mode" : tạo nhánh mới và di chuyển đến nhánh đó

"git checkout -b pink-mode" : tạo nhánh mới và di chuyển đến nhánh đó

  

**LƯU** **Ý**_:_ +) commit trước khi chuyển sang nhánh khác

+) Kiểm tra .git folder và kiếm tra HEAD đang chỉ đâu

**b) Ghép các nh****ánh trong git**

Các thao tác để gộp hai nhánh: ta đã tạo ra 1 nhánh khác là nhánh nav-bar. Hiện tại ta có 2 nhánh là: **m****aster** và **branch**. Ta mong muốn gộp nhánh **nav-b****ar** vào nhánh **m****aster.**

>> git switch master # chuyển đến nhánh ta mong muốn gộp vào

>> git merge nav-bar # gộp nhánh ta muốn gộp vào master

>> git log —oneline # kiểm tra xem merge có thành công không

![](https://beta.appflowy.cloud/api/file_storage/ff47d52f-3fb3-44ec-95fe-a0a2f689b195/v1/blob/b17a92cf%2D01e4%2D4777%2D9df2%2D6c6bb1f5a8d4/QpkvF737Gr420Zf2zqO_AplTabO8AZm-Z_3zN-m1IBw=.png)  
![](https://beta.appflowy.cloud/api/file_storage/ff47d52f-3fb3-44ec-95fe-a0a2f689b195/v1/blob/b17a92cf%2D01e4%2D4777%2D9df2%2D6c6bb1f5a8d4/0sTEUEazsUVxU9xhqZYUddCnx7tgsHP7WUVtQfeiOkI=.png)

**Graph của repo sau khi merge**

>> git branch -d nav-bar # xóa đi branch nav-bar sau khi merge

Tại sao lại cần phải xóa đi? Tại vì sau khi merge thì nav-bar lúc này sẽ không còn được dùng đến. Ta nên xóa để số branch chúng ta có thể truy cập có thể giảm đi⇒ giảm độ phức tạp

  

**c) Mâu thuẫn giữa hai nhánh**

Ví dụ: Đạt tạo nhánh con tên là fix-bug có file main.cpp y hệt với nhánh chính master. Du thay đổi file main.cpp ở nhánh master và Đạt cũng thay đổi file main.cpp trong nhánh fix-bug. Hai thay đổi này là **khác nhau** ⇒ **git kh****ông bi****ết nên gi****ữ lại thay** **đổi n****ào khi m****erge hai nhánh với nhau** **⇒** **m****âu thuẫn (c****onflict)**

Ta sẽ sửa trong vscode luôn khi có mâu thuẫn

  

3. **KẾT NỐI VỚI GITHUB**

Các bước:

- Tạo github repo trên git (public hoặc private)

Đặt origin

git remote add origin [_**https://github.com/username/myproject.git**_](https://github.com/username/myproject.git)

Chọn nhánh main

git branch -M main

Push code

git push -u origin main

Khi mà để repo private cần tạo ra 1 cái key

nếu kết nối bằng https chỉ cần nhập username và mã key được cấp

  

Thói quen tốt cần có:

Luôn git pull origin main để code base được cập nhật

  

4. **CHỨC NĂNG CỦA GIT**

a) git diff : so sánh sự khác biết

git diff —staged : so sánh sự khác biệt giữa file hiện tại và giai đoạn staging

git diff 8310f08 04aa235 : so sánh sự khác biệt giữa 2 commit

![](https://beta.appflowy.cloud/api/file_storage/ff47d52f-3fb3-44ec-95fe-a0a2f689b195/v1/blob/b17a92cf%2D01e4%2D4777%2D9df2%2D6c6bb1f5a8d4/E9qb7jck6AvwwGrJpLaeCmBqMTOQI9CkVFfd7jgGovc=.png)  

b) git stash

![](https://beta.appflowy.cloud/api/file_storage/ff47d52f-3fb3-44ec-95fe-a0a2f689b195/v1/blob/b17a92cf%2D01e4%2D4777%2D9df2%2D6c6bb1f5a8d4/g7Fo97c2Ly8Cps8HClkh_vu9hXb3FrImeJLW9-pDjgY=.png)

c) Xem lại commit cũ

![](https://beta.appflowy.cloud/api/file_storage/ff47d52f-3fb3-44ec-95fe-a0a2f689b195/v1/blob/b17a92cf%2D01e4%2D4777%2D9df2%2D6c6bb1f5a8d4/4hBIjsiKLQQYpMq3mdyil2p2prPeGHoOGdTTK2uXhZ8=.png)

d) REBASE (chức năng nguy hiểm chỉ thực hiện khi hiểu mình đang làm gì

ta có 1 nhánh như sau master A-B-C-D

và nhánh con add-greet A- E-G

sau khi rebase project sẽ trở thành một đường thẳng không như merge làm ta phải tạo thêm 1 node có hai cha. Nhưng sau khi rebase thì cái nhánh add-greet sẽ dẫn đầu chứ không phải master

ta sẽ có A-B-C-D-E-G trong đó commit đến add-greet tạo thành đường thẳng nếu commit tới master tạo ra

A-B-C-D-E-G

|—-H