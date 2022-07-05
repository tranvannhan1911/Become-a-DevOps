# Virtual Machine

- What is virtualization?
    - Là phân chia máy vật lý (physical machine) thành nhiều máy ảo (virtual machine), mỗi máy ảo sẽ chứa riêng biệt, OS riêng, storage riêng,…
- Trước khi virtualization ra đời.
    - Mỗi service, mỗi application phải chạy trên 1 server (1 physical machine).
    - Các tài nguyên của server không được sử dụng triệt để, gây lãng phí.
    - Phải cấu hình, vận hành, duy trì từng server.
- Các thuật ngữ (terminologies)
    - Host OS: là hệ điều hành chính của physical machine
    - Guest OS: là hệ điều hành của virtual machines
    - VM: virtual macchines
    - Snapshot: là tạo bản backup của virtual machine
    - Hypervisor: là công cụ hay phần mềm cho phép tạo các VM
- Các loại hypervisor
    - Type 1
        - Thường sử dụng trong production
        - VMware esxi, Xen hypevisor
    - Type 2
        - Thường sử dụng để học, testing
        - Oracle virtualbox, VMware server
- Create VM
    
    [VM - Create Virtual Machine](Virtual%20Machine%20c62c1388324448e2a6c42a03fe74be3e/VM%20-%20Create%20Virtual%20Machine%2023917c09962647ffaac0dab2e2bc18e8.md)