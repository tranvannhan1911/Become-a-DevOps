# VM - Create Virtual Machine

1. Theo cách thủ công
    1. Cài đặt VirtualBox
        
        ```bash
        $ choco install vagrant
        ```
        
    2. Tạo VM
        1. Tạo
            
            ![Untitled](VM%20-%20Create%20Virtual%20Machine%2023917c09962647ffaac0dab2e2bc18e8/Untitled.png)
            
        2. Memory size: `1GB`
        3. Hard disk: `Create a virtual hard disk now`
        4. Hard disk file type: `VDI (VirtualBox Disk Image)`
        5. Storage on physical hard disk
            
            ![Untitled](VM%20-%20Create%20Virtual%20Machine%2023917c09962647ffaac0dab2e2bc18e8/Untitled%201.png)
            
        6. Tải file iso: `http://mirrors.vhost.vn/centos/7.9.2009/isos/x86_64/` > `CentOS-7-x86_64-Minimal-2009.iso`
        7. Chọn `my-centos7` > `settings` > `storage` > `Controller: IDE` > `Empty`
            1. Chọn vị trí file iso
            2. Chọn `Live CD/DVD`
        8. Chọn `my-centos7` > `settings` > `network` > `adapter 2`
            1. Enable
            2. Chọn `Bridge Adapter` > `Intel Dual Band Wireless-AC 8265`
                - `Bridge Adapter` sẽ cho phép lấy ip từ route
2. Tạo tự động bằng Vagrant
    1. Vagrant là gì?
        - Vagrant là một công cụ tự động ra đời để quản lý vòng đời của các máy ảo (VM). Cho phép tạo MV, sửa MV, xóa, quản lý,…
    2. Trước khi Vagrant ra đời
        - Phải tự cài đặt hệ điều hành
        - Mỗi khi tạo VM phải làm theo cách thủ công và lặp đi lặp lại.
        - Mỗi khi muốn tạo lại một VM từ một VM tương tự khác cũng phải làm thủ công từ đầu.
        - Tạo VM theo cách thủ công sẽ làm mất thời gian.
    3. Chức năng của Vagrant
        - Không cần cài đặt hệ điều hành.
        - Setup VMs thông qua Images (trong Vagrant được gọi là `vagrant boxes`)
        - Vagrant boxes có sẵn trên Vagrant Cloud.
        - Quản lý VMs thông qua `Vagrantfile`. Các thay đổi về cấu hình tự động cũng thông qua file này
        - Cung cấp các câu lệnh, scripts để quản lý VMs.
    4. Vagrant Architecture
        
        ![cmcglobal.udemy.com_course_decodingdevops_learn_lecture_26460448.png](VM%20-%20Create%20Virtual%20Machine%2023917c09962647ffaac0dab2e2bc18e8/cmcglobal.udemy.com_course_decodingdevops_learn_lecture_26460448.png)
        
    5. Vagrant Setup
        - VT được bật trong BIOS
        - Cài đặt Vagrant Tool
            
            ```bash
            $ choco install vagrant
            ```
            
        - Hypervisor như Oracle Virtualbox.
        - CLI như GIT bash
    6. Cách sử dụng Vagrant (Cài đặt ubuntu 18)
        1. Tạo thư mục project `./vagrant/ubuntu18` thư mục này sẽ chứa Vagrantfile.
            
            ```bash
            $ mkdir vagrant
            $ mkdir vagrant/ubuntu18
            $ cd vagrant/ubuntu18
            ```
            
        2. Tìm kiếm Vagrant boxes ở trên Vagrant Cloud ([https://app.vagrantup.com/boxes/search](https://app.vagrantup.com/boxes/search))
            - Tìm kiếm `ubuntu 18`
                
                ![Untitled](VM%20-%20Create%20Virtual%20Machine%2023917c09962647ffaac0dab2e2bc18e8/Untitled%202.png)
                
            - Copy box name `ubuntu/bionic64`
        3. Vagrant init
            
            ```bash
            $ vagrant init ubuntu/bionic64
            ```
            
            - Vagrantfile sẽ được tạo
                
                ```bash
                # -*- mode: ruby -*-
                # vi: set ft=ruby :
                
                # All Vagrant configuration is done below. The "2" in Vagrant.configure
                # configures the configuration version (we support older styles for
                # backwards compatibility). Please don't change it unless you know what
                # you're doing.
                Vagrant.configure("2") do |config|
                  # The most common configuration options are documented and commented below.
                  # For a complete reference, please see the online documentation at
                  # https://docs.vagrantup.com.
                
                  # Every Vagrant development environment requires a box. You can search for
                  # boxes at https://vagrantcloud.com/search.
                  config.vm.box = "ubuntu/bionic64"
                
                  # Disable automatic box update checking. If you disable this, then
                  # boxes will only be checked for updates when the user runs
                  # `vagrant box outdated`. This is not recommended.
                  # config.vm.box_check_update = false
                
                  # Create a forwarded port mapping which allows access to a specific port
                  # within the machine from a port on the host machine. In the example below,
                  # accessing "localhost:8080" will access port 80 on the guest machine.
                  # NOTE: This will enable public access to the opened port
                  # config.vm.network "forwarded_port", guest: 80, host: 8080
                
                  # Create a forwarded port mapping which allows access to a specific port
                  # within the machine from a port on the host machine and only allow access
                  # via 127.0.0.1 to disable public access
                  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
                
                  # Create a private network, which allows host-only access to the machine
                  # using a specific IP.
                  # config.vm.network "private_network", ip: "192.168.33.10"
                
                  # Create a public network, which generally matched to bridged network.
                  # Bridged networks make the machine appear as another physical device on
                  # your network.
                  # config.vm.network "public_network"
                
                  # Share an additional folder to the guest VM. The first argument is
                  # the path on the host to the actual folder. The second argument is
                  # the path on the guest to mount the folder. And the optional third
                  # argument is a set of non-required options.
                  # config.vm.synced_folder "../data", "/vagrant_data"
                
                  # Provider-specific configuration so you can fine-tune various
                  # backing providers for Vagrant. These expose provider-specific options.
                  # Example for VirtualBox:
                  #
                  # config.vm.provider "virtualbox" do |vb|
                  #   # Display the VirtualBox GUI when booting the machine
                  #   vb.gui = true
                  #
                  #   # Customize the amount of memory on the VM:
                  #   vb.memory = "1024"
                  # end
                  #
                  # View the documentation for the provider you are using for more
                  # information on available options.
                
                  # Enable provisioning with a shell script. Additional provisioners such as
                  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
                  # documentation for more information about their specific syntax and use.
                  # config.vm.provision "shell", inline: <<-SHELL
                  #   apt-get update
                  #   apt-get install -y apache2
                  # SHELL
                end
                ```
                
                - `config.vm.box = "ubuntu/bionic64"`: box
                - `config.vm.box_check_update = false`: để tắt tự động cập nhật
                - `config.vm.network "forwarded_port", guest: 80, host: 8080`: Cho phép forward port từ host machine sang guest machine. Điều này cho phép công khai truy cập dựa trên port của host machine.
                - `config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"`: Cho phép forward port từ host machine sang guest machine. Chỉ cho phép truy cập thông qua 127.0.0.1 hoặc localhost.
                - `config.vm.network "private_network", ip: "192.168.33.10":` Tạo private network chỉ có host mới có thể truy cập vào địa chỉ IP này
                - `config.vm.network "public_network"`: Tạo public network cho guest machine. Được tạo thông qua WIFI/LAN. Guest machine được cung cấp IP như một máy vật lý trong mạng.
                - `config.vm.synced_folder "../data", "/vagrant_data"`: Chia sẻ thư mục cho VM
                - `vb.gui = true`: Hiển thị VirtualBox GUI khi khởi động machine
                - `vb.memory = "1024"`: Kích thước memory của VM
                - `config.vm.provision "shell", inline: <<-SHELL`: Các script được chạy khi tạo VM.
        4. Create VM
            
            ```bash
            $ vagrant up
            ```
            
            - Lần đầu khởi chạy thì vagrant sẽ tải box từ Vagrant Cloud về sau đó tạo VM
            - Lần tiếp theo khởi chạy nếu VM đang tắt thì sẽ được bật trở lại.
            - 
        5. Truy cập vào VM
            
            ```bash
            $ vagrant ssh
            ```
            
        6. Reboot VM
            
            ```bash
            $ vagrant reboot
            ```
            
        7. Tắt VM
            
            ```bash
            $ vagrant halt
            ```
            
        8. Xóa VM
            
            ```bash
            $ vagrant destroy
            ```