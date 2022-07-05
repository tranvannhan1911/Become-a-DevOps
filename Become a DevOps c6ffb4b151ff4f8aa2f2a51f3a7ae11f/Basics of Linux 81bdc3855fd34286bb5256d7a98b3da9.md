# Basics of Linux

1. Giới thiệu về Linux
    1. Linux là gì?
        - Là một hệ điều hành mã nguồn mở hoặc một Kernel mã nguồn mở
        - Được tạo ra nằm 1991 bởi Linus Torvalds
        - Linux được phát triển tương tự như UNIX kernel cùng với GNU utilities.
    2. Các nguyên tắc Linux (Linux Principles)
        - Mọi thứ được lưu trữ dưới dạng file (kể cả phần cứng): Như chuột, bàn phím,…
        - Small Single purpose Programs
        - Có khả năng liên kết các chương trình với nhau để thực hiện các công việc phức tạp.
        - Tránh giao diện người dùng bị khóa: Tránh việc phải chờ sự phản hồi của người dùng trên giao diện.
        - Các cấu hình được lưu trữ trên các file text. Dễ dàng sửa đổi, cấu hình
    3. Tại sao lại sử dụng Linux
        - Mã nguồn mở
        - Có cộng động rộng lớn hỗ trợ
        - Hỗ trợ đa dạng đối với phần cứng
        - Hầu hết các server đều chạy trên Linux
        - Dễ dàng làm các công việc một cách tự động trên Linux.
        - Bảo mật tốt.
    4. Kiến trúc của Linux
        
        ![Untitled](Basics%20of%20Linux%2081bdc3855fd34286bb5256d7a98b3da9/Untitled.png)
        
    5. Các bản phân phối Linux phổ biến
        - Ubuntu Linux
        - Linux Mint
        - Arch Linux
        - Fedora
        - Debian
        - OpenSuse
    6. Các hệ điều hành server Linux phổ biến
        - Red Hat Enterprise Linux
        - Ubuntu Server
        - Centos
        - SUSE Enterprise Linux
    7. Các thư mục quan trọng
        - Home: `/root`, `/home/username`
        - User Executables: `/bin`, `/usr/bin`, `/usr/local/bin`
            - Các câu lệnh như `ls`, `cat`, `pwd`,…
            - Được sử dụng bởi các người dùng bình thường
        - System Executables: `/sbin`, `/usr/bin`, `/usr/local/sbin`
            - Các câu lệnh phía hệ thống như `adduser`, `apt`,…
            - Được sử dụng bởi root user.
        - Các ổ cứng: `/media`, `/mnt`
        - Các file cấu hình: `/etc`
        - Các file tạm sẽ được xóa khi reboot: `/tmp`
        - Kernel và Bootloader: `/boot`
        - Dữ liệu: `/var`, `/srv`
            - Webserver, database,…
        - Thông tin hệ thống: `/proc`, `/sys`
        - Các thư viện được chia sẻ: `/lib`, `/usr/lib`, `/usr/local/lib`
2. File trong Linux
    1. Các loại file trong Linux
        - `-`: File text hoặc file binary
        - `d`: Thư mục
        - `l`: Liên kết (shortcut)
        - `c`: File đặc biệt, sử dụng cho input hoặc output như các file trong thư mục /dev
        - `s`: File socket
        - `p`: Pipe, cho phép tiến trình tương tác với nhau mà không sử dụng network socket semantics.
        - `b`: Block file
    2. Các câu lệnh file cơ bản
        
        ```bash
        # đọc file
        $ cat <path to file>
        
        # hiển thị file/folder
        $ ls
        
        # hiển thị kể cả file/folder ẩn
        $ ls -a
        
        # hiển thị file/folder dưới dạng danh sách và sắp xếp theo thời gian mới đến cũ
        $ ls -lt
        
        # hiển thị file/folder dưới dạng danh sách và sắp xếp theo thời gian cũ đến mới
        $ ls -ltr
        
        # hiển thị file/folder dưới dạng danh sách
        $ ll
        
        # tạo thư mục,
        $ mkdir folder1 folder2
        
        # tạo thư mục theo nhiều level
        $ mkdir -p folder1/folder2/folder3
        
        # Tạo file
        $ touch <path to file>
        
        # Tạo nhiều file: devopsfile1.txt, devopsfile2.txt,...
        $ touch devopsfile{1..10}.txt
        
        # copy file
        $ cp <path to file source> <path to folder destination>
        
        # copy folder
        $ cp -r <path to folder source> <path to folder destination>
        
        # di chuyển file
        $ mv <path to file source> <path to folder destination>
        
        # di chuyển folder
        $ mv <path to folder source> <path to folder destination>
        
        # đổi tên file/folder: đổi tên filea thành fileb
        $ mv filea fileb
        
        # with regular expression: move tất cả các file kết thúc bằng .txt vào thư mục dest
        $ mv *.txt dest/
        
        # xóa file
        $ rm file1.txt
        
        # xóa folder
        $ rm -r folder1
        
        # hiển thị thông tin của file, loại file,...
        $ file <path to file>
        
        # link file
        $ ln -s <path to file source> <path to folder destination>
        ```
        
        - Vim editor
            - Command mode
                - `gg`: Lên đầu file
                - `G`: Tới cuối file
                - `w`: Chuyển trỏ chuột đi tới, theo từng từ
                - `b`: Chuyển trỏ chuột đi người lại, theo từng từ
                - `nw`: Di chuyển tới `n` từ (ví dụ: 5w)
                - `nb`: Di chuyển ngược lại `n` từ (ví dụ: 5b)
                - `u`: undo thay đổi mới nhất (theo từ)
                - `U`: undo thay đổi mới nhất (theo dòng)
                - `Ctrl+R`: redo thay đổi
                - `yy`: copy một dòng
                - `nyy`: copy `n` dòng (ví dụ: 5yy)
                - `dd`: Cắt dòng
                - `ndd`: Cắt `n` dòng
                - `p`: Dán dòng bên dưới con trỏ chuột
                - `P`: Dán dòng bên trên con trỏ chuột
                - `dw`: Xóa từng ký tự (giống nút xóa)
                - `x`: Xóa từng ký tự (giống nút delete)
                - `/`: Tìm kiếm
                    - `n`: Đến vị trí tìm kiếm tiếp theo
                    - `N`: Đến vị trí tìm kiếm trước đó
            - Extend mode
                - Bắt đầu bằng ký tự `:`
                - `:w`: Lưu file
                - `:q`: Thoát file
                - `:q!`: Thoát file mà không lưu
                - `:se nu`: hiển thị dòng
3. Filter & Redirection
    1. Các câu lệnh filter
        
        ```bash
        # find text in file, return lines contain, sensitive
        $ grep text file1.txt
        
        # find text in file, return lines contain, not sensitive
        $ grep -i text file1.txt
        
        # find text in current folder, return lines contain, not sensitive
        $ grep -iR text *
        
        # return lines not contain the text, not sensitive, 
        $ grep -iv text file1.txt
        
        # reader, can scroll page, search,...
        $ less file1.txt
        
        # reader
        $ more file1.txt
        
        # show 10 first lines of file
        $ head file1.txt
        
        # show 20 first lines of file
        $ head -20 file1.txt
        
        # show 10 last lines of file
        $ tail file1.txt
        
        # show 20 last lines of file
        $ tail -20 file1.txt
        
        # show dynamic content, automatic show when file is updated
        $ tail -f file1.txt
        
        # show first column that seperate by :
        $ cut -d: -f1 /etc/passwd
        
        # replace all aaaa to bbbb and print, not save
        $ sed 's/aaaa/bbbb/g' file1.txt
        
        # replace all aaaa to bbbb and print, save
        $ sed -i 's/aaaa/bbbb/g' file1.txt
        ```
        
    2. Redirection
        
        ```bash
        # replace ouput to file
        $ date > date.txt
        
        # append ouput to file
        $ date >> date.txt
        
        # not print,  not append to file
        $ sudo apt install python > /dev/null
        
        # append error message to file
        $ dateeee 2>> error.txt
        
        # append output and error message to file
        $ dateeee &>> error.txt
        
        # Piping, đếm số file, thư mục trong thư mục hiện tại
        $ ls | wc -l
        
        # Tìm các file có tên bắt đầu bằng host
        $ find /etc -name host*
        ```
        
4. Users & Group
    1. Nội dung
        - User và Group được sử dụng để kiểm soát truy cập files, tài nguyên
        - 
    2. Các câu lệnh
        
        ```bash
        # Chuyển qua người dùng root
        $ sudo -i
        
        # Hiển thị người dùng hiện tại
        $ whoami
        
        # logout current user
        $ exit
        
        # 
        ```
        
5. Các câu lệnh khác
    - Hiển thị thông tin hệ điều hành
        
        ```bash
        $ cat /etc/os-release
        NAME="Ubuntu"
        VERSION="20.04.4 LTS (Focal Fossa)"
        ID=ubuntu
        ID_LIKE=debian
        PRETTY_NAME="Ubuntu 20.04.4 LTS"
        VERSION_ID="20.04"
        HOME_URL="https://www.ubuntu.com/"
        SUPPORT_URL="https://help.ubuntu.com/"
        BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
        PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
        VERSION_CODENAME=focal
        UBUNTU_CODENAME=focal
        ```
        
    - Xem thông tin RAM, CPU
        
        ```bash
        $ free -m
                      total        used        free      shared  buff/cache   available
        Mem:           3872         104        3552           0         215        3553
        Swap:          1024           0        1024
        ```
        
6. Sudo
7. Software Management
8. Services & Processes
9. Server Management